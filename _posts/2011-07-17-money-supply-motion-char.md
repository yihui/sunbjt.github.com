--- 
layout: post
title: "2006\xE5\xB9\xB4\xE8\x87\xB3\xE4\xBB\x8A\xE5\x9B\xBD\xE5\x86\x85\xE8\xB4\xA7\xE5\xB8\x81\xE4\xBE\x9B\xE5\xBA\x94\xE9\x87\x8F\xE7\x9A\x84Motion Chart"
tags: 
- chart
- google
status: publish
type: post
published: true
category:
  - R Graphics
---
<a href="http://www.bjt.name/wp-content/uploads/2011/07/motion-chart.png">
</a>在2008年，第一届中国R语言会议上，来自于艾瑞咨询的张翔为大家展示了一组极具震撼力的泡泡图，而这段视频便是Hans Rosling 在2006年 <a href="http://www.ted.com/talks/hans_rosling_shows_the_best_stats_you_ve_ever_seen.html" rel="nofollow">TED</a> 上的演讲，讲述的是1956年-2006年之间各国间的经济发展变化。虽然个人认为泡泡图的实现的技术并没有太多技术含量，但惊讶于Hans Rosling大智若愚的演讲能力，甚至再看完五六遍之后，仍然还会被其感染。

再后来， Hans Rosling将这款数据展示产品卖给了Google，而Google又将其整合到<a href="http://code.google.com/apis/visualization/documentation/gallery.html" rel="nofollow">Visualisation API</a> 里，于是我们可以调用Google的API来使用这些有趣的图形展示功能。

更令人鼓舞的是：前不久，Markus Gesmann, Castillo两位老大，写了<a href="http://cran.r-project.org/web/packages/googleVis/" target="_blank">googleVis</a>这个R扩展包，将Hans Rosling的泡泡图同R语言完美的整合在了一起:)

下面就是在R语言里，通过<a href="http://cran.r-project.org/web/packages/googleVis/" target="_blank">googleVis</a>包，对我国2006年至今的货币供应量（M0、M1、M2）Motion Chart（将横坐标设置为time以后，点击Play）


![](http://www.bjt.name/wp-content/uploads/2011/07/motion-chart.png)


碎碎念：从泡泡的跳动上看，央行投放的货币供应量（亿元）在2009-2011年间，增加的最为剧烈，当然这个时间段也是房价近十年间增长最为迅速的两年。
而现在呢，房市开始限购，国内房地产市场已经撑不住超发的货币，因此广泛的通货膨胀开始蔓延。引用郎咸平的几段话：

*  我们近几年发了76.5万亿的货币,是GDP的2.5倍,而美国的货币量除上GDP只是0.6,只有我们的四分之一
*  唯一的解释只能是货币的购买力在下降,这就是经济学里的通货膨胀


最后，关于<a href="http://cran.r-project.org/web/packages/googleVis/" target="_blank">googleVis</a>包的使用请移步至<a href="http://code.google.com/p/google-motion-charts-with-r/" target="_blank">这里</a>。
