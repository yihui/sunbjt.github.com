--- 
layout: post
title: "\xE4\xB9\x9F\xE7\x9C\x8B\xE9\x9B\x86\xE6\x99\xBA\xE5\xA4\xB4\xE8\x84\x91\xE9\xA3\x8E\xE6\x9A\xB4\xE8\xAE\xBA\xE5\x9D\x9B\xE7\x9A\x84\xE6\xA0\xB8\xE5\xBF\x83\xE7\xBB\x84\xE7\xBB\x87"
tags: 
- networks
- sna
status: publish
type: post
published: true
category:
  - R Graphics
---
<a href="http://www.swarmagents.cn/" target="_self">集智俱乐部</a>是我最近两年来比较关注的俱乐部，尤其集智在三号会所的线下活动，一帮来自五湖四海、背景迥异的年轻人，因为一个共同感兴趣的主题，各抒己见（头脑风暴），过程非常奇妙。至今依然清晰的记得第一次参加集智活动时，大家对超自然（超能力）现象的热烈讨论。说实话，当时刚听完报告，还以为进入一个邪教组织了，呵呵～～

2010年12月9日，集智俱乐部的 计算士 和 Jake 发布了<a href="http://www.swarmagents.cn/bs/viewforum.asp?id=14358&amp;UrlTail=" target="_self">头脑风暴论坛数据分析报告(全文)</a>。报告很有趣，其中讲到了 Zipf 定律和以社会网络分析为主的网络骨架图。Jake 同时将头脑风暴论坛的数据<a href="http://www.swarmagents.cn/thesis/detail.asp?id=350" target="_self">发布</a>，数据为XML格式文件。而我，恰恰对头脑风暴论坛的兴趣也是非常浓厚，所以这边本地将这些数据处理了一下（大家可参考<a href="http://bjt.cos.name/wp-content/uploads/2010/12/sw_data.rar" target="_self">这里</a>），并作了一些简单分析同大家分享。

首先是头脑风暴论坛中最为关键的几个actors：<a href="http://bjt.cos.name/wp-content/uploads/2010/12/key-actors-1.png"><img class="aligncenter size-full wp-image-10731" title="key actors 1" src="http://bjt.cos.name/wp-content/uploads/2010/12/key-actors-1.png" alt="" width="672" height="672" /></a>

这里考虑了两个因素，网络的 Eigenvector Centrality 和 Betweenness Centrality（即vertex和edge信息），从上图看：jake 的地位最高，且Eigenvector和Betweenness相差较小；紧随其后的是东方隐，当然这个紧随其后是指相对概念。

由于 jake 的地位（重要到有点儿离群点的意思了），其他会员的状态不是很明显，所以考虑将 jake 这点去掉：

<a href="http://bjt.cos.name/wp-content/uploads/2010/12/key-actors-2.png"><img class="aligncenter size-full wp-image-10730" title="key actors 2" src="http://bjt.cos.name/wp-content/uploads/2010/12/key-actors-2.png" alt="" width="672" height="672" /></a>这样处理以后，除 jake 和 东方隐 以外的用户状态浮出。如果主观上增加“第二梯队”的概念（除去jake和东方隐两人，个人对头脑风暴论坛不是很熟悉，权且这么划分。当然也可以做个聚类啥的，不折腾了），那么属于这一梯队的ID包括：zcard2000、ruiaijun、黄淼鑫、计算士、Michael0607、天狮星11、飞鸟、yywwkk等。

问题来了，论坛上这些比较重要的actors是如何组织在一起（相互作用）的呢？
<p style="text-align: center;"><a href="http://bjt.cos.name/wp-content/uploads/2010/12/sw.png"><img class="aligncenter size-full wp-image-10728" style="border: 1px solid black;" title="The Network of swarmagents" src="http://bjt.cos.name/wp-content/uploads/2010/12/sw.png" alt="" width="653" height="653" /></a>上图为重要节点的网络图，不难看出：jake 在头脑风暴论坛的地位是无可替代的，牢牢地占据论坛关系中最核心的位置（估计这种结构在<a href="http://cos.name/bbs" target="_blank">COS论坛</a>也同样存在，其中的核心不用我多言，哈～～）</p>
还有就是东方隐这个节点也非常有意思，需要关注。但详细的说明，这里就省略了，毕竟对头脑风暴论坛不像<a href="http://cos.name" target="_blank">统计之都</a>那么熟悉，硬搬着去解释，难免贻笑大方。简单陈述一下绘制关系图的原则：
<ul>
	<li>同计算士绘制的骨架图一样，这里也同样将一些不太重要的节点做了删除处理（subgraph），只留下了重要节点的骨架；</li>
	<li>骨架中的节点也并不是每一个都做了展示，而是通过 Eigenvector 和 Betweenness 的对比，将差异比较明显的节点做（名称）展示。而表示为红色的节点大小即为二者差异的大小。</li>
</ul>

********

### 写在最后：

这篇文章实际上写的非常仓促，有很多细节考虑不是很完备，并且从数据上看，
能够展现的也不止上面的一些信息（比如发帖时间的分析、还有一些条件密度类的内容，等等）。
但与其无限期放在草稿箱里，不如直接放出来。因此这篇文章可能会有比较大的改动（主要是绘图部分），
但什么时候，就不得而知了。

如果有集智俱乐部的童鞋看到这篇文章的话，多多指正，并——欢迎在[统计之都](http://cos.name)上讨论。

### 关于集智俱乐部：

>2003 年，集智俱乐部创始人张江（Jake）创办了集智俱乐部网站，该网站一直致力于宣传、普及、推广复杂系统科学，并展开广泛的跨学科交流，俱乐部渐渐聚集了一批有识之士。 5 年后的 2008 ，集智俱乐部的交流和活动开始从虚拟世界走向现实，并尝试发展一个现实世界中的学术组织。目前集智俱乐部的日常管理工作由集智核心成员负责， 主要活动有开放式的讲座与交流，以及其它主题小组活动。……
