--- 
layout: post
title: "\xE6\x95\xB0\xE6\x8D\xAE\xE6\x8C\x96\xE6\x8E\x98\xE4\xB9\x8BR\xE4\xB8\x8ESQL"
tags: 
- datamining
- Oracle
- SQL
status: publish
type: post
published: true
category:
  - Data Mining
---
今天看到老同学<a href="http://weibo.com/n/JulieJulieJulieJulie" target="_blank">@JulieJulieJulieJulie</a> 的<a href="http://www.tudou.com/programs/view/g52FYAg63Kg/" target="_blank">浪漫求婚</a>，真的很浪漫、很唯美、很感动。正如评论说的，我们又相信爱情了！于是，小兴奋，睡不着，爬起来补一篇文章。

*****
正文开始


最近在数据挖掘专业网站 KDnuggets 上刊出了2011年度关于数据挖掘/分析语言流行度的<a href="http://www.kdnuggets.com/2011/08/poll-languages-for-data-mining-analytics.html" target="_blank">调查</a>，不出意料R、SQL、Python果然排在了前三位。当然有看官说了，参与调查的样本数量太少，而且以登录KDnuggets网站的用户为主，样本的信息显然是有偏的。实话说，我也对KDnuggets网站的Poll持保留态度，但它的结果毕竟代表了某一类人群的使用偏好，尤其是在语言角度。


<a href="http://bjt.cos.name/wp-content/uploads/2011/08/182924.png"><img class="aligncenter" title="data mining survey" src="http://bjt.cos.name/wp-content/uploads/2011/08/182924.png" alt="" width="492" height="305" /></a>


我们看排名前5位的语言：


* `R`：世界范围内的标准统计语言，以快速更新的算法，灵活的编程，广泛的扩展，绚丽的图形著称，遵循GPL协议的开源软件
* `SQL`：大部分企业使用的，数据仓库、集市的通用查询语言，在大型数据应用上有极大的优势，同时也是数据分析/挖掘的基础
* `Python`：传说中的Google的三大开发语言，适用于粘合一些复杂应用，我这里工作暂时没有涉及过
* `Java`：太多的应用都基于Java的，不然Oracle也不会花上74亿美元收购SUN了
* `SAS`：曾经的数据分析领域老大，当然现在市场份额依旧非常高。但SAS昂贵的使用费用迫使更多的分析工作者转到了开源领域，比如R


后四种语言同R语言还都有一些关系，闲扯起来还真是没完没了，这里就不再赘述，各位可以在搜索引擎上搜索R+XXX。
如果我们将范围限制在数据挖掘这个主题，R同SQL的关系则变得非常非常紧密。


众所周知，R的强项在于灵活的算法，以及开发速度，但其所有的计算都是在内存中进行，一旦数据量达到了内存上限，基本上就是叫天天不灵，
叫地地不应了。所以在使用R做数据挖掘时，就必须考虑使用其他的数据工具弥补R在这方面的劣势。尤其是在商业应用上，
不能搭建R环境的条件下，SQL语言是提供挖掘结果的不二选择。


支持SQL的商用数据库比如Oracle、DB2性能优异，但对系统的占用非常厉害，假如本地装了Oracle，又开了点其他应用，2G的内存很快就会吃到1.5G甚至以上，
再想用R做分析那只能用“捉襟见肘”这个词来形容了。当然如果在办公条件下有相应的服务器环境最好，
在某些应用环境下，甚至可以通过本地多开R进程来达到并行计算的目的。


或者本地分析比较多，但数据量又时常上到百兆，虽然R也能够处理，但依然建议将数据移植到本地构建的轻量数据库环境，比如MySQL环境。
从我的经验上看，虽然MySQL对比Oracle、DB2来说小巧很多，但在同R语言配合的本地应用上，性能更加有保证。


有了支持SQL的数据库环境，就要聊一聊R语言到底和SQL有什么关系：


<ul>
	<li>各大数据库厂商已经开发了相关的支持R语言的数据挖掘套件，比如Oracle的<a href="http://ftp.ctex.org/mirrors/CRAN/web/packages/RODM/index.html">RODM</a>，Teradata的 <a id="download-6865-7769-0" href="https://downloads.teradata.com/download/applications/teradata-r/1.0">teradataR</a>等。</li>
	<li>R本身就可以通过扩展包来对数据库执行SQL，这时你可以把R语言作为调度环境。R的计算过程结果可以直接作为参数传递到数据库中，并将相应的结果返回，供R环境使用。</li>
	<li>通过sqldf包，在R内部使用标准SQL对数据进行预处理，包括group by，order by，join，where等操作。</li>
	<li>当然R最重要的用途是将数据挖掘的结果转义为标准SQL语言，利用数据库来实现挖掘结果。当然有人说了，不是有pmml可以将模型嵌入到数据库么？！扯！到现在我也没见pmml成为应用标准，老老实实的将模型结果转义到SQL才是王道。比如用于概率预测的Logistic回归或者分类模型的Tree-based Models，这些模型的转义工作都不难，这样最终的工程实施都脱离了R环境，更具通用性，且利用了数据库的高速性能。</li>
</ul>

*****
说句题外话：不知道哪位看官见过70万字符长度的庞大SQL语句——是的，你没看错，70w，R转义的，可以执行，对于数据库而言不过是半分钟的事情。
