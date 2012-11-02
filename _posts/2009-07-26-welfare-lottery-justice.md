--- 
layout: post
title: "\xE4\xBB\x8E\xE4\xB8\x80\xE7\xAD\x89\xE5\xA5\x96\xE5\x87\xBA\xE7\x8E\xB0\xE7\x9A\x84\xE6\xA6\x82\xE7\x8E\x87\xE7\x9C\x8B\xE4\xB8\xAD\xE5\x9B\xBD\xE7\xA6\x8F\xE5\x88\xA9\xE5\xBD\xA9\xE7\xA5\xA8\xE7\x9A\x84\xE5\x85\xAC\xE6\xAD\xA3\xE6\x80\xA7"
tags: 
- datamining
- "\xE6\xB3\x8A\xE6\x9D\xBE\xE5\x88\x86\xE5\xB8\x83"
status: publish
type: post
published: true
category:
  - Data Mining
meta: 
  _edit_last: "2"
  _wp_old_slug: welfare-lottery
  _efficient_related_posts: "a:5:{i:0;a:4:{s:2:\"ID\";s:5:\"10715\";s:10:\"post_title\";s:36:\"\xE5\x8F\xB2\xE4\xB8\x8A\xE6\x9C\x80\xE5\xBC\xBA\xE6\x82\x8D\xE7\x9A\x84\xE6\x95\xB0\xE6\x8D\xAE\xE6\x8C\x96\xE6\x8E\x98\xE4\xBB\x8B\xE7\xBB\x8D\";s:7:\"matches\";s:1:\"2\";s:9:\"permalink\";s:54:\"http://www.bjt.name/2010/12/toronto-data-mining-intro/\";}i:1;a:4:{s:2:\"ID\";s:5:\"10654\";s:10:\"post_title\";s:34:\"Oracle\xE6\x95\xB0\xE6\x8D\xAE\xE5\xBA\x93\xE5\xBC\x80\xE5\xA7\x8B\xE6\x94\xAF\xE6\x8C\x81R\xE8\xAF\xAD\xE8\xA8\x80\";s:7:\"matches\";s:1:\"2\";s:9:\"permalink\";s:49:\"http://www.bjt.name/2010/06/oracle-data-mining-r/\";}i:2;a:4:{s:2:\"ID\";s:5:\"10306\";s:10:\"post_title\";s:27:\"\xE6\x8F\x90\xE9\xAB\x98\xE5\x8F\x8C\xE8\x89\xB2\xE7\x90\x83\xE4\xB8\xAD\xE5\xA5\x96\xE6\xA6\x82\xE7\x8E\x87\";s:7:\"matches\";s:1:\"2\";s:9:\"permalink\";s:41:\"http://www.bjt.name/2009/11/thunder-ball/\";}i:3;a:4:{s:2:\"ID\";s:4:\"9992\";s:10:\"post_title\";s:36:\"\xE5\x85\xB3\xE4\xBA\x8E\xE5\x9C\xA8hoopchina\xE4\xB8\x8A\xE5\x8F\x91\xE5\xB8\x96\xE7\x9A\x84\xE5\x9B\x9E\xE7\xAD\x94\";s:7:\"matches\";s:1:\"2\";s:9:\"permalink\";s:59:\"http://www.bjt.name/2009/04/hoopchina-single-index-yaoming/\";}i:4;a:4:{s:2:\"ID\";s:4:\"9997\";s:10:\"post_title\";s:27:\"500\xE4\xB8\x87\xEF\xBC\x9F\xE5\x8E\xBB\xE4\xB9\xB0\xE5\x8F\x8C\xE8\x89\xB2\xE7\x90\x83\xEF\xBC\x81\";s:7:\"matches\";s:1:\"2\";s:9:\"permalink\";s:104:\"http://www.bjt.name/2009/05/500%e4%b8%87%ef%bc%9f%e5%8e%bb%e4%b9%b0%e5%8f%8c%e8%89%b2%e7%90%83%ef%bc%81/\";}}"
  _relation_threshold: "2"
  dsq_thread_id: "609163407"
---
<a href="http://news.sina.com.cn/s/2009-07-08/215318181309.shtml">深圳福彩3000万巨奖诈骗案</a>发生后，好多朋友开始质疑中国福利彩票的公正性，并向我询问福利彩票是不是真的如传闻那样--福利彩票自产自销？。由于身在中福彩的原因，很多支持福彩公正的内情不太合适发布在网上，但--数据一汇总，上帝也会发笑。这篇博文从一等奖中奖概率分布的角度给各位童鞋聊聊福彩的公正性。

现在每一期的福彩双色球销售额大概是2亿左右（已持续很长时间），每注双色球为2元，就是说每期双色球的销售大概会有1亿人次参与。

<span style="font-family: Courier New;"><samp style="font-family: 宋体;">在随机选择，且每次抽取都是等概率的的假定条件下，理论的重复彩票注数的分布（0注至41注）如下：</samp></span>

<span style="font-family: Courier New;"><samp style="font-family: 宋体;"><img src="http://www.bjt.name/wp-content/uploads/1.png" alt="" width="644" height="371" /></samp></span>

<span style="font-family: Courier New;"><samp><span style="font-family: Arial;">
</span></samp></span>

一等奖是完全随机出现的，那么<span style="font-family: Courier New;"><samp><span style="font-family: Arial;">在假设条件下，一等奖同时出现五注的概率最高，六注、四注其次，再次为七注、三注，类推……当然理论上，没有中奖（0注）和中12注以上的概率相比其他情形低了很多。</span></samp></span>

<span style="font-family: Courier New;"><samp><span style="font-family: Arial;">那么我们再看一看福利彩票双色球每期中一等奖（2008年1月1日至2009年7月23日）的实际分布情况：</span></samp></span>

<span style="font-family: Courier New;"><samp><img src="http://www.bjt.name/wp-content/uploads/2009/07/thunderball2.png" alt="thunderball2.png" width="623" height="401" /></samp></span>

<span style="font-family: Courier New;"><samp><span style="font-family: Arial;">
有童鞋看出端倪了：实际数据的分布同理论上的分布是不一致的！理论上的一等奖出现概率最大在出现五注的位置，而实际上一等奖出现的最大概率出现在了两注的位置。</span></samp></span>

<span style="font-family: Courier New;"><samp><span style="font-family: Arial;">为什么会出现这样的情况？主要是因为我们最开始的假设是有问题。</span></samp></span>

<span style="font-family: Courier New;"><samp><span style="font-family: Arial;">双色球每期销售会有1亿人次的彩民参与？不可能！双色球的覆盖度没有那么大。</span></samp></span>

<span style="font-family: Courier New;"><samp><span style="font-family: Arial;">一些彩民为了提高中奖概率（或者说迷信一些选号方法），会采用"复式"、"胆拖"、"倍投"等方式投注，当然大部分彩民还是会老老实实的买一注。综合考虑到这些因素以后，凭经验估计样本量应该为现在的一半左右，即5000万。这样看来较为合理的一等奖中奖概率理论上分布为：</span></samp></span>

<span style="font-family: Courier New;"><samp><span style="font-family: Arial;"><img src="http://www.bjt.name/wp-content/uploads/2.png" alt="" width="644" height="371" /></span></samp></span>

此时理论分布同实际分布已经非常相似。

实际双色球一等奖分布的右边尾巴上恰恰显示了"复式"、"胆拖"、"倍投"的投注效果。

再插一句：

<a href="http://news.sina.com.cn/c/2009-07-25/035216009956s.shtml">深圳福彩3000万大奖诈骗犯身份曝光</a>一文中提到：
<blockquote>警方调查发现，程某先是编写了一个可以自动运行的木马软件，然后利用与福彩中心合作的机会，进入福彩中心机房，植入自动运行的木马程序。一旦摇奖结果出来，这个程序会自动将程某所购买的彩票修改成一等奖的号码。</blockquote>
这里可以推测程某天真地以为满足兑大奖的条件为：
<ol>
	<li>数据库里的数据正确；</li>
	<li>实体彩票存在。</li>
</ol>
恩，没有问题！但，这两个条件可是通过<strong>很多很多很多</strong>的手段来监管的。
