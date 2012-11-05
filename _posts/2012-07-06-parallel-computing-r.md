--- 
layout: post
title: "并行化你的运算-初识parallel包"
tags: 
- high performance computing
- parallel
status: publish
type: post
published: true
category:
  - R Computing
---
R 2.14.0版本以后，parallel包被作为核心包引入R，这个包主要建立在 multicore 和 snow 包的工作基础之上，包含了这两个包大部分功能函数，以及集成了随机数发生器。


实际上对于R来说，并行化可以在不同的层级上实现：比如，在最底层，现在的多核CPU可以实现一些基础的数值运算（比如整数和浮点算数）；
高级一点的，一些扩展BLAS包使用多线程并行处理向量和矩阵的操作，甚至有些R扩展包，通过调用OpenMP（注释1）或pthreads来使用C 级别的多线程方式。


本文的主角，parallel包却是从另外角度的实现，简单说是一种“粗粒度”的并行化方式。在我们的日常工作中会遇到一下情况：


*  在不同的数据集上应用相同的R函数
*  bootstrap计算


对于第一种情况，一般会采用显式循环或隐式循环的方式，但可惜的是R并不能识别这是并行计算，依旧按照串行的方式进行处理。
第二种情况，如蒙特卡洛模拟，但在同一个R进程中，所有的运算都是按顺序进行的，唯一能做的就是多开几个R，将各个运算人工分配，最后手工合并结果，囧


我们再仔细考虑一下第一种情况（第二种情况也类似），关键在于这些计算并不关联，或者说不需要进行通讯。这样的计算过程可以使用如下方式来表述：


*  启动M个附属进程，并初始化
*  针对于任务，为每个附属进程分发所有的数据
*  将任务粗略的分为M个块儿（chunks），并将这些块儿发送到附属进程（包含需要的R代码）
*  等待所有的附属进程完成计算任务，并返回结果
*  对于其他任务也同样重复2-4
*  关闭附属进程


对于上述的并行化方式，附属进程可以使用如下方式构建：


*  通过system("Rscript")或类似方式，原理即在同一台或类似的机器上开启一个完全相同的R安装程序，而后在主、副进程间通过sockets通讯。这种方式在所有的R平台上都可以使用，snow包就实现了这种方式。</li>
*  通过forking。Fork是可移植操作系统（POSIX operating system）上的概念，这种方式适用于除Windows以外的所有平台。它的做法是创建一个新的完全拷贝主进程的副进程，包括workspace以及其他状态（如随机数流）。这种拷贝方式在内存页面发生变化前是共享内存的，因此速度很快。但这种方式也有缺点，它共享了整个进程，甚至包括GUI元素。这可能会导致一些bug。multicore包则实现了这种方式。</li>


当然，对于这两种并行化方式，最新的R自带的parallel包都有支持。
还有一种是通过OS级的通讯方式，比如PVM (`parallel virtual machine')，以及SGE等，同样有相关的技术和包来支持，这里不再展开讨论。


我们现在说一些实际的，如何在实际项目应用中使用并行化计算方式来提高我们的工作效率。
在parallel包里，对应上述两种并行化方式有如下两个核心函数（针对于lapply函数的并行化，mclapply在windows上不能使用）：


*  parLapply(cl, x, FUN, ...)
*  mclapply(X, FUN, ..., mc.cores)


考虑 lapply这个函数，这种隐式循环函数，它实际就是对不同的数据应用了相同的函数，是可以并行化的。首先看一个例子：


    doit <- function(x)(x)^2 + 2*x
    system.time(res <- lapply(1:5000000,  doit))
    user system elapsed
    24.05 0.05 24.20


上述lapply的表达同一个for循环没什么两样，但由于数据集比较大，500w，所以消耗的时间相对较长。我们使用parallel包来加速：


    library(parallel)
    cl <- makeCluster(getOption("cl.cores", 3)) # use 3 cores
    system.time(res <- parLapply(cl, 1:5000000,  doit))
    user system elapsed
    6.54 0.34 19.95
    stopCluster(cl) # close clusters


运行parLapply的时候，处理器三个核心瞬间占满，很快就将结果返回。不过这个函数有两点要注意：


*  首先要先用detectCores函数确定系统核心数目，对于Window系统下的Intel I5或I7 处理器，一般使用detectCores(logical = F)来获得实际的物理核心数量。</li>
*  由于这个函数使用的是调用Rscript的方式，这个例子里，对象被复制了三份，因此内存会吃的很厉害，在大数据条件就要小心使用</li>


在Linux下使用mclapply函数的效果如下：


    mc <- getOption("mc.cores", 3)
    system.time(res <- mclapply(1:5000000,  doit, mc.cores = mc))
    user system elapsed
    6.657 0.500 7.181


除了对于lapply，sapply这类函数的并行化外，parallel包还有针对于apply的并行化函数，比如parApply，
以及各类动态平衡的函数如parLapplyLB，请参见parallel包的帮助文档。

注释1：OpenMPOpen Multiprocessing is 
an [API](href="http://en.wikipedia.org/wiki/Application_programming_interface) that 
supports multi-platform [Shared memory](http://en.wikipedia.org/wiki/Shared_memory) 
[Multiprocessing](http://en.wikipedia.org/wiki/Multiprocessing) programming 
in [C (programming language)](http://en.wikipedia.org/wiki/C_(programming_language)),
[C++](http://en.wikipedia.org/wiki/C%2B%2B), [Fortran](http://en.wikipedia.org/wiki/Fortran) 
on most [Processor architecture](http://en.wikipedia.org/wiki/Processor_architecture) and 
[Operating system](http://en.wikipedia.org/wiki/Operating_system).

