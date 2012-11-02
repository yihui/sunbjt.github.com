--- 
layout: post
title: "\xE6\x9B\xBC\xE5\xBE\xB7\xE5\xB8\x83\xE6\xB4\x9B\xE7\x89\xB9\xE9\x9B\x86"
tags: 
- Mandelbrot set
- "\xE7\xAE\x97\xE6\xB3\x95"
status: publish
type: post
published: true
category:
  - R Graphics
meta: 
  _edit_last: "2"
  _relation_threshold: ""
  _efficient_related_posts: a:0:{}
  dsq_thread_id: "600836813"
---
前一段时间，John Baez 在自己的主页上更新了一篇文章名为 <a href="http://math.ucr.edu/home/baez/roots/">The Beauty of Roots</a>，这篇文章之后在“科学松鼠会”上被 <a title="《多项式的根之美》" href="http://songshuhui.net/archives/23604.html" target="_blank">转载</a>。上面提到了曼德布洛特集（<a href="http://en.wikipedia.org/wiki/Mandelbrot_set"><strong>Mandelbrot set</strong></a>），根据其发明者法国数学家 <a title="Benoît Mandelbrot" href="http://commons.wikimedia.org/wiki/Beno%C3%AEt_Mandelbrot">Benoît Mandelbrot</a> 而命名。

曼德布洛特集是一种分形，从一般分形性质来说：
<blockquote>客观自然界中许多事物，具有自相似的“层次”结构，在理想情况下，甚至具有无穷层次。适当的放大或缩小几何尺寸，整个结构并不改变。不少复杂的物理现象，背后就是反映着这类层次结构的分形几何学。</blockquote>
常见的曼德布洛特集是这个样子（分辨率原因，部分细节显示不够）：

<a href="http://bjt.cos.name/wp-content/uploads/2009/12/scale1.png"><img class="aligncenter size-full wp-image-10438" title="scale1" src="http://bjt.cos.name/wp-content/uploads/2009/12/scale1.png" alt="" width="480" height="480" /></a>

假如我们把这个集合的下半部分（最下边的小块）分割出来，就是这个样子（8倍放大）：

<a href="http://bjt.cos.name/wp-content/uploads/2009/12/scale2.png"><img class="aligncenter size-full wp-image-10438" title="scale2" src="http://bjt.cos.name/wp-content/uploads/2009/12/scale2.png" alt="" width="480" height="480" /></a>

由于分辨率的提高，所以显示了第一幅图中并没有显示的细节。

继续放大，上图的左上部分的那个小枝（6倍放大）：

<a href="http://bjt.cos.name/wp-content/uploads/2009/12/scale41.png"><img class="aligncenter size-full wp-image-10446" title="scale4" src="http://bjt.cos.name/wp-content/uploads/2009/12/scale41.png" alt="" width="480" height="480" /></a>

再把上图最靠近左边的那个小枝——放大（50/3倍放大）：

<a href="http://bjt.cos.name/wp-content/uploads/2009/12/scale51.png"><img class="aligncenter size-full wp-image-10447" title="scale5" src="http://bjt.cos.name/wp-content/uploads/2009/12/scale51.png" alt="" width="480" height="480" /></a>

继续放大最左边的小枝，似乎在末端又出现了一个类似的小枝（5倍放大）：

<a href="http://bjt.cos.name/wp-content/uploads/2009/12/scale6.png"><img class="aligncenter size-full wp-image-10450" title="scale6" src="http://bjt.cos.name/wp-content/uploads/2009/12/scale6.png" alt="" width="480" height="480" /></a>

如果继续放大下去可能还是这个样子 ：）

注释：
<ol>
	<li>最后一张图相比第一张图来说相当于局部放大了 4000 倍。</li>
	<li>高质量的矢量绘图数据量比较大，R 处理起来有些问题，只好使用局部放大的方式。</li>
	<li>更多的使用其他软件绘制图形可以见：http://commons.wikimedia.org/wiki/Mandelbrot_set</li>
</ol>
最后广告一枚：

<a href="http://cos.name/bbs/thread.php?fid=27">COS 统计图形和可视化版</a> ——<a href="http://cos.name/bbs/read.php?tid=17644">用 R 玩分形</a>。
