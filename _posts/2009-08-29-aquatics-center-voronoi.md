--- 
layout: post
title: "\xE6\xB0\xB4\xE7\xAB\x8B\xE6\x96\xB9\xE5\x92\x8C Voronoi \xE5\x8E\x9F\xE7\x90\x86"
tags: 
- voronoi
status: publish
type: post
published: true
category:
  - R Graphics
---
还记得第一次看到<a href="http://en.wikipedia.org/wiki/Beijing_National_Aquatics_Center">水立方</a>时的惊讶么？

是什么这么吸引我们？是有如天空般的颜色？还是那气泡似的形状？
<p style="text-align: center;"><a href="http://bjt.cos.name/wp-content/uploads/2009/08/Watercube.jpg"><img class="size-full wp-image-10624 aligncenter" title="Watercube" src="http://bjt.cos.name/wp-content/uploads/2009/08/Watercube.jpg" alt="" width="800" height="462" /></a></p>
从水立方的外墙结构上看，不但外观美观，而且十分紧凑。水立方外墙为什么会有这样的性质，是因为它上应用了一项最优化的技术，即<a href="http://en.wikipedia.org/wiki/Voronoi" target="_blank">Voronoi</a> 原理。

<a href="http://en.wikipedia.org/wiki/Voronoi" target="_blank">Voronoi</a> 图也常常被称为 Dirichlet 格局（Dirichlet tessellation）。通俗讲，其原理是一项从点到面的技术。它的每个多边形只有一个"生成点"，而这个多边形上的每个点到"生成点"的距离总是比到其他"生成点"的距离要小（是不是想到了 K-means 算法？）。
<div style="page-break-after: always;"><span style="display: none;"> </span></div>
在建筑设计上，有设计人员争论这类方法定义为“参数化设计”。认为这种方法不能同传统的、依靠灵感的设计方式相比，因为这种方法高度依赖计算机，只需要简单改变若干参数就能得到设计方案。但这个论断，恰恰忽略了“参数化设计”背后的数学意义。

既然 <a href="http://en.wikipedia.org/wiki/Voronoi" target="_blank">Voronoi</a> 是一种最优化的算法，那么除在建筑学上给我们带来的美轮美奂的视觉效果外，它在空间统计上同样也有应用。

下面，我根据各个省会城市（包括香港、澳门）的地理位置，利用 Voronoi 原理，计算每个省最佳控制范围（使用红色的线条标记）：

<img src="http://bjt.cos.name/wp-content/uploads/2009/08/China.png" alt="China.png" width="700" height="490" />

虽然理论值（最优）和现实值（行政区划、地理）总有差距，但是，比较一下会发现一些值得探讨的现象：
<ul>
	<li>
<div>内蒙古应该好好的规划一下，从东边到西边实在太远了，把西边的划给宁夏可能好点；东边划给北京、东三省；</div></li>
	<li>
<div>河北北部，不论是属于北京还是天津都会好些，记得我小的时候，宁可去北京、天津，也不乐意去遥远的省会--石家庄；</div></li>
	<li>
<div>青海应该把甘肃的北部包括进去；</div></li>
	<li>
<div>上海、香港、澳门有一部分管辖区也也不错么：）</div></li>
</ul>
整体上看，大部分省的行政区划还是符合 Voronoi 原理。也就是说，单纯从空间距离的角度来看，我国的行政区划还是比较不错的。，
