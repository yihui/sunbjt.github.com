--- 
layout: post
title: "R语言环境下的文本挖掘"
tags: 
- topic model
- text mining
- tm
- XML
status: publish
type: post
published: true
---
上一篇文章说道最近我在做文本挖掘方面的一些工作，到今天为止暂告一段落。刚好也整理了一份针对中文的《R语言环境下的文本挖掘》，
供感兴趣的童鞋参考（见文章底部）。


自然语言处理（Nature Language Process）是一个非常让人着迷的领域，应用范围非常广泛，
比如去年人机大战中大出风头的IBM Watson，iPhone 4S的语音助理模块Siri，
以及针对于社会热点的舆情分析，这些应用都使用了自然语言处理技术。
当然，统计背景的分析类科研人员更关注于舆情分析这类的文本挖掘技术。


很多统计软件都提供了文本挖掘的功能，比如常见的数据分析软件SAS、SPSS等，
下图是文本挖掘工具及特性的一个总结（来自于Journal of Statistical Software 2008）


![](http://www.bjt.name/wp-content/uploads/2012/03/tools.png)


* Preprocess：数据准备、导入、清洗以及一般性的预处理
* Associate：关联分析，根据同时出现的频率找出关联规则
* Cluster：将相似的文档（词条）进行聚类
* Categorize：将文本划分到预先定义的类别里
* API：可扩展的应用编程接口


至少在2008年，商业和开源软件的功能特性差不多
（但我不确认Latent Semantic Analysis、Latent Dirichlet Allocation这类的模型是否支持），
只是由于众所周知的缘故，对于API的扩展支持有所差异。


对于中文环境下的文本挖掘，无外乎要解决如下几个问题：

* 较为精确的中文分词（可能还需要支持个性化题库，甚至词性分析）
* 生成词条-文档矩阵，甚至矩阵的运算
* 后续的挖掘算法支撑（传统的以及语义类的）
* 其他


在R语言环境下，有众多的包支撑解决上述问题。
Ingo Feinerer开发维护的[tm](http://ftp.ctex.org/mirrors/CRAN/web/packages/tm/index.html)包提供了完整的文本挖掘的框架，
借助辅助工具及R包，甚至还可以处理word、pdf文档的读入，文档处理并行化运算，文件数据库的语料处理等问题。


闲话不多说，最下面链接给出了一份基于《Introduction to the tm Package》整理的，基于tm包的中文文本挖掘的介绍性文档，内容包含


* 互联网网页处理：XML包的简介
* 中文分词
* tm包的完整介绍：读写、语料库构建、过滤、转化、元数据、文档-词条矩阵等
* 文本挖掘技术及应用等


当然，作为非正式发布文档还有很多地方不尽完善，后续可能会有较大更新，请关注博客上的to do list。

文档下载：[R语言环境下的文本挖掘](http://www.bjt.name/wp-content/uploads/2012/03/Text-Mining-in-R.pdf)
