--- 
layout: post
title: "\xE6\x95\xB0\xE9\x87\x8F\xE5\xBA\x9E\xE5\xA4\xA7\xE7\x9A\x84\xE5\x8C\x85\xEF\xBC\x8C\xE5\xA4\x8D\xE6\x9D\x82\xE7\x9A\x84\xE7\xBD\x91\xE7\xBB\x9C"
tags: 
- networks
- sna
status: publish
type: post
published: true
category:
  - R Graphics
---
<a href="http://www.r-project.org">R</a> 各个镜像中的 <a href="http://ftp.ctex.org/mirrors/CRAN/web/packages/" target="_blank">Contributed Packages</a> 越来越多，截至今日，已经达到1950个，单单拉动鼠标把所有的 包名 从 A 到 Z 过一遍也得 10 几秒。随便考你一道：最后一个 R 包是啥？

zoo？

呵呵，我的印象里一直是它，仔细瞧了瞧发现是个叫 <a href="http://ftp.ctex.org/mirrors/CRAN/web/packages/zyp/index.html">zyp</a> 的包。

又一次领略了 R 强大的扩展能力撒？这个特点给我们带来了一些烦恼，因为人类的大脑能够理解的概念是有限的，对于没有任何关联的概念，我们的识别能力一般不超过 7，而且 R 的涵盖范围实在太广。从我们的有限性（7个概念）和 R 的无限性这一角度讲，逐一认识这些包几乎是不可能的！不过还好，至少我们可以可以参考 <a href="http://cran.r-project.org/mirrors.html" target="_blank">CRAN</a> 上的 <a href="http://ftp.ctex.org/mirrors/CRAN/web/views/" target="_blank">Task Views</a>，大致了解 R 包的使用方向。

我们换个思路，不是从 R 的使用方向上，而是从 R 包的依赖关系上？

这些 R 包并不是相互独立的。比如说，MASS 包依赖于 R (&gt;= 2.5.0), grDevices, graphics, stats, utils 这些基础包；而又会有包依赖于 MASS 包，比如 <a href="http://yihui.name/" target="_blank">yihui</a> 的 <a href="http://ftp.ctex.org/mirrors/CRAN/web/packages/animation/index.html">animation </a>，当然还有可能有包依赖于 <a href="http://ftp.ctex.org/mirrors/CRAN/web/packages/animation/index.html">animation</a> ……

遍历所有的包，我们就看到了一个网络，一个 <a href="http://www.r-project.org">R</a> 包的网络。

为了简化起见，这里忽略了同其他包没有关系的包（当然并不是完全没有关系，所有的包都和 <a href="http://www.r-project.org">R</a> 或 <a href="http://www.r-project.org">R</a> 的基础包有关，如果这样计量的话，会导致所有的包都会指向 R）。

首先截取了这个庞大网络的一部分：
<p style="text-align: center;"><img class="aligncenter" src="http://bjt.cos.name/wp-content/uploads/2009/09/sna.png" alt="sna.png" width="630" height="578" /></p>
从上图我们可以看到，标记点为215、271的两个包是我们研究的包网络中的两个关键点，这两个包分别是lattice、mvtnorm。

关于这两个包：
<ol>
	<li>
<div>lattice：网格绘图的基础包。很多包基于它扩展并不惊讶吧；</div></li>
	<li>
<div>mvtnorm：多元正态分布和t分布的概率密度函数、累计分布函数、分位数函数、分布随机数。多元分布的基础。</div></li>
</ol>
从 271（mvtnorm）向左上，又会有一个小的聚集。那个小的聚集中心（110），是 fBasics 包，如果各位对金融领域关注的话，应该知道它在其中的地位吧。

当然，由于抽取的是一个子网络，很多的连接都被生硬地隔断，因此出现了大量的孤立点。

如果我们把 CRAN 上的1950个包都放到我们的网络中会是这样：
<p style="text-align: center;"><a href="http://bjt.cos.name/wp-content/uploads/2009/09/sna_black.png"><img class="aligncenter size-full wp-image-10794" title="R cran packages networks" src="http://bjt.cos.name/wp-content/uploads/2009/09/sna_black.png" alt="" width="800" height="500" /></a></p>


<hr />

最后说明：
<ol>
	<li>第一张图的 包 id 换成 包名称 会导致 演示的视觉效果很差，网页又不支持 pdf 直接显示，只好把带包名的图放这（<a href="http://bjt.cos.name/wp-content/uploads/sna300.pdf">pdf</a>）。</li>
	<li>带包名的 ，1950 个包的全图就算了吧，单绘图就得 2 分钟，更别提调整参数了 ……</li>
</ol>
