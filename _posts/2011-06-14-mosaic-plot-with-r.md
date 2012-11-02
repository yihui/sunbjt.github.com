--- 
layout: post
title: "\xE7\x94\xA8R\xE5\xAE\x9E\xE7\x8E\xB0\xE9\xA9\xAC\xE8\xB5\x9B\xE5\x85\x8B\xE6\x8B\xBC\xE5\x9B\xBE"
tags: 
- mosaic
status: publish
type: post
published: true
category:
  - R Graphics
---
又是一个R不务正业的例子。

三天前，<strong><a href="http://cos.name/cn/profile/371112">itux</a> </strong>在统计之都论坛上问到了如何做 <a href="http://www.matrix67.com/blog/archives/519" target="_blank">Matrix67</a> 博客上的平滑马赛克图，我是好事之徒，颠颠地跑去瞧了一眼。恩，蛮有意思的，而且非常黄，非常暴力！但比较悲剧的是我不会用Mathematica，只好用R实现了一下。

本来想标题改的彪悍一些——《一千二百个女人和我的故事》，想想还是算了吧，虽说是用了1200个漂亮女人组成了我的头像，但她们我一个也不认识，哈哈。

<a href="http://bjt.cos.name/wp-content/uploads/2011/06/me.png"><img class="aligncenter size-full wp-image-10802" title="it is me" src="http://bjt.cos.name/wp-content/uploads/2011/06/me.png" alt="" width="750" height="1000" /></a>

用的原图我就不贴了，实际上我是戴着眼镜的，马赛克平滑以后，不明显了。

最后是<a href="http://bjt.cos.name/wp-content/uploads/2011/06/main.r" target="_blank">代码</a>。非常简单，不到20行。大概所需要的时间：构思写代码1个小时，下载和整理图片时间长点，3个多小时（当然你本地资源和<a href="http://www.matrix67.com/blog" target="_blank">Matrix67</a>一样丰富的话另说，哈）。
