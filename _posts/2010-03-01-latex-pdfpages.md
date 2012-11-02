--- 
layout: post
title: "\xE7\x94\xA8LaTeX\xE6\x94\xBE\xE5\xA4\xA7pdf\xE6\x96\x87\xE6\xA1\xA3"
tags: 
- ESLII
- LaTeX
status: publish
type: post
published: true
meta: 
  _edit_last: "2"
  _efficient_related_posts: a:0:{}
  _relation_threshold: ""
  dsq_thread_id: "600837282"
---
2009年12月，hastie教授主页上更新了勘误后的The Elements of Statistical Learning II。这部机器学习领域的巨著，做数据挖掘或者统计分析的同行应该比较熟悉，不过这本书在美帝的 Amason 上要卖 80$，非常不符合中国特色的社会主义！

好在 Hastie 几位大牛深刻体会广大发展中国家莘莘学子的购买能力，在其<a href="http://www-stat.stanford.edu/~tibs/ElemStatLearn/">主页</a>上提供了免费的pdf版本。不过pdf版本有个小问题：排版是为了a4打印而设计的，白边太多，在电脑上看或者打印出来极为不爽。

下面提供一个解决方案来处理这个问题——使用LaTeX中的pdfpages宏包。
具体LaTeX代码参考如下：
<pre lang="LATEX">
\documentclass[a4paper,12pt]{report}
\usepackage[final]{pdfpages}
\begin{document}
\includepdf[pages=19-26, scale=1.3,
delta=0mm 5mm, frame]{ESLII_print3.pdf}
\end{document}
\endinput
</pre>
使用PDF LaTeX编译。
主要参数非常简单，即从ESLII_print3.pdf中提取第19至26页（第一章），并放大1.3倍（成功剔除掉多余的白边）。
