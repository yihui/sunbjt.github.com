--- 
layout: post
title: "费波那西数列和递归"
tags: 
- Fibonacci
- Julia
status: publish
type: post
published: true
category:
  - R Computing
---
前段时间在老家给小舅子补习高中数学，其中有一道数列的求解，题目是这样的：


*  a_1 = 1</li>
*  a_2 = 1</li>
*  a_n = a_(n-1) + a_(n-2)</li>


求 a_n 的通项表达。

解题思路是先构建等比数列 b_n，再将等比数列 b_n 变形回 a_n ，求得通项。
这道题实际就是费波那西数列的初等代数求法。费波那西数列在科学、自然界等很多领域都有表现，
比如我们常说的黄金分割比（1.618），即是两个相邻费波那西数的比值


`f(n + 1)/f(n) = (1 + sqrt(5))/2`


还有美丽的向日葵的花盘中果实：

![](http://bjt.cos.name/wp-content/uploads/2012/05/sunflower.jpg)


这个序列虽说非常有意思，但我当时并没有意识到在R中求解费波那西序列的时间问题。

首先看一下，最为原始的、朴素的R代码：


    fib <- function(n)
    {
    ifelse(n < 2, n, fib(n - 1) + fib(n - 2))
    }
    system.time(fib(25))


所需的时间是1.65s，时间相当长，那我们进行一下改写：


    fib2 <- function(n)
    {
    if(n < 2) n else Recall(n-1) + Recall(n-2)
    }
    system.time(fib2(25))


所需时间是0.21s，通过改进if else 及 recall 得到了一定提升，但仍然非常慢，继续：


    library(compiler)
    enableJIT(3)
    fib3 <- cmpfun(fib2)
    system.time(fib3(25))


需要0.19s，通过byte code编译方式，时间略微有所缩短，但依旧很慢。看来在R环境下，最高性能也就如此了。那试一试在R中调用C++代码的方式：


    require(inline)
    incltxt <- '
    int fibonacci(const int x) {
    if (x == 0) return(0);
    if (x == 1) return(1);
    return (fibonacci(x - 1)) + fibonacci(x - 2);
    }'
    fibRcpp <- cxxfunction(signature(xs="int"),
    plugin="Rcpp",
    incl=incltxt,
    body='
    int x = Rcpp::as<int>(xs);
    return Rcpp::wrap( fibonacci(x) );
    ')
    start <- Sys.time()
    fibRcpp(25)
    end <- Sys.time()
    end - start


这里用system.time已经不能正确显示时间（显示为0秒），稍稍改了下格式，现在需要时间是0.07s（调用inline包，在R环境下编译C++）。

是否还能够优化，答案是肯定的，直接上C。刚好有个gmp包刚好可以求费波那西数列，它是C语言级别的求解：


    library(gmp)
    start <- Sys.time()
    fibnum(25)
    end <- Sys.time()
    end - start


所需时间进一步降低，为0.027s。那有看官说了，难道R语言在处理递归就这么不济？这不调用底层语言的话，性能也太寒碜了吧。其实不然，来个杀手锏（来自于R inforno，稍稍有点难理解）      


    fibonacci <- local({                      
      memo <- c(1, 1, rep(NA, 100))           
      f <- function(x) {                      
        if(x == 0) return(0)                  
        if(x < 0) return(NA)                  
        if(x > length(memo))                  
        stop("’x’ too big for implementation")
        if(!is.na(memo[x])) return(memo[x])   
        ans <- f(x-2) + f(x-1)                
        memo[x] <<- ans                       
      ans                                     
    }                                         
    })                                        
    start <- Sys.time()                       
    fibonacci(25)                             
    end <- Sys.time()                         
    end - start                               


时间是0.033s，略逊于调用优化了的C，但明显强于非优化的C++。还没完，实际上此序列是有线性算法的，大囧：    


    fib = function (x)           
    {                            
            if (x == 0)          
                    return (0)   
            n1 = 0               
            n2 = 1               
            for (i in 1:(x-1)) { 
                    sum = n1 + n2
                    n1 = n2      
                    n2 = sum     
            }                    
            n2                   
    }                            
    start <- Sys.time()          
    fib(25)                      
    end <- Sys.time()            
    end - start                  



所需时间是0.026s，基本上和优化的C一致。还能再快吗！！？？是的，还能。本文的最开头提到费波那西数列的初等代数求法，最终序列的通项可以用以下式子表示：  

    s <- sqrt(5)                         
    fn <- function(n){                   
    s/5 * (((1 + s)/2)^n - ((1 - s)/2)^n)
    }                                    
    fibn <- cmpfun(fn)                   
    start <- Sys.time()                  
    fibn(25)                             
    end <- Sys.time()                    
    end - start    

                      
时间定格在0.019s，世界终于清静了……

（注：gmp包中的求解方式没有详细考证C代码，貌似也是线性解法）

__参考资料__

*  [费波那西序列](http://en.wikipedia.org/wiki/Fibonacci_number">http://en.wikipedia.org/wiki/Fibonacci_number)
*  [R中的递归](http://stackoverflow.com/questions/6807068/why-is-my-recursive-function-so-slow-in-r)
*  [julia和R讨论](http://www.johnmyleswhite.com/notebook/2012/03/31/julia-i-love-you/)


