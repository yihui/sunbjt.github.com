--- 
layout: post
title: "\xE5\x95\x86\xE4\xB8\x9A\xE6\x95\xB0\xE6\x8D\xAE\xE5\xBA\x93\xE5\xAF\xB9R\xE8\xAF\xAD\xE8\xA8\x80\xE7\x9A\x84\xE6\x94\xAF\xE6\x8C\x81"
tags: 
- IBM
- Netezza
- Oracle
- SAP
- SAS
status: publish
type: post
published: true
category:
  - Big Data
---
一直以来，我们在提到使用R进行数据分析、数据挖掘都会使用RODBC、RJDBC、DBI等相关的包来调用数据库，比如我前面罗嗦的一片文章<a href="http://www.bjt.name/2011/08/r-and-sql-datamining/"><span style="color: #0000ff;"><strong>数据挖掘之R与SQL</strong></span></a>，但实际基本上各大数据库厂商已有相应的R语言企业级应用产品，这些厂商包括Oracle、IBM、Teradata、Sybase、SAP。


<h3>Oracle R Enterprise</h3>


Oracle R Enterprise是针对于大数据市场下，用于处理日益丰富的数据。这款产品有以下优势：
##### 企业级的R应用
<ul>
	<li>允许DBA将R语言模型产品化</li>
	<li>可以将R模型整合到BI仪表盘（BIEE）</li>
	<li>统计学家可以直接使用数据库，而不需去了解具体SQL</li>
	<li>减少Oracle数据库外的数据管理成本</li>
</ul>
##### 减少高昂SA$的使用费用
<ul>
	<li>可完全替代SA$ base，节省SA$的使用年费</li>
	<li>分析人员可以直接面对数据库进行个性化分析，而不需要数据导出</li>
	<li>超过100内置的统计函数可以同Base SA$兼容</li>
</ul>
##### 大数据分析的in-database支持
<ul>
	<li>高性能的代数运算(在R中整合<a href="http://software.intel.com/en-us/articles/intel-mkl/">Intel's Math Kernel Library</a>)</li>
	<li>R语句的执行的使用并行化运算方式（包括扩展包）</li>
	<li>高度整合了R语言快速开发、数据库并行计算的优势</li>
</ul>
众所周知，R语言将数据置于内存，数据处理能力有限，Oracle R Enterprise将此瓶颈完全打开，并将性能提升到更高级别。

<a href="http://www.bjt.name/wp-content/uploads/2012/04/image.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="image" src="http://www.bjt.name/wp-content/uploads/2012/04/image_thumb.png" alt="image" width="322" height="348" border="0" /></a>


<h3><a href="http://www-01.ibm.com/common/ssi/rep_ca/2/897/ENUS212-042/ENUS212-042.PDF">IBM Netezza®</a></h3>


Netezza 并不隶属于IBM原有产品线，而是针对于“一体机”市场，于2010年17亿美元的价格收购获得，用以扩张其用于销售、市场营销和产品开发的商务分析产品。Netezza对R语言的支持，主要通过Revolution合作，通过调用<a href="http://www.revolutionanalytics.com/products/revolution-enterprise-for-ibm-netezza.php"><strong>R Enterprise from Revolution® Analytics</strong></a>平台来实现。Netezza的特点可以总结为：可扩展的、高性能的、大规模内置并行分析平台。

<a href="http://www.bjt.name/wp-content/uploads/2012/04/image1.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="image" src="http://www.bjt.name/wp-content/uploads/2012/04/image_thumb1.png" alt="image" width="543" height="321" border="0" /></a>

注：除了R语言外，Netezza还支持SAS、PASW等分析软件
<h3><a href="http://www-01.ibm.com/software/data/infosphere/biginsights/">IBM® InfoSphere® BigInsights</a></h3>
IBM BigInsights 同样也整合了R语言资源，提供了Map-Reduce架构的R语言并行化计算环境，包括了大数据集的文本挖掘和机器学习算法。BigInsights可以将构建的R语言模型发布在Hadoop平台上（同IBM Netezza一样，通过调用<a href="http://www.revolutionanalytics.com/products/revolution-enterprise-for-ibm-netezza.php"><strong>R Enterprise from Revolution® Analytics</strong></a>），极大的满足企业级数据需求。

<a href="http://www.bjt.name/wp-content/uploads/2012/04/image2.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="image" src="http://www.bjt.name/wp-content/uploads/2012/04/image_thumb2.png" alt="image" width="553" height="345" border="0" /></a>

注：为IBM提供R语言商业化应用的公司是Revolution，关于这家公司可以参考<a href="http://www.bjt.name/2009/10/spss-norman-nie-r/" target="_blank">这里</a>。


<h3>SAP HANA</h3>


借助SAP BusinessObjects Predictive Analysis平台，分析师们既可以使用内置的预测性算法来构建模型，也可以整合并使用流行的开源数据统计分析语言——R语言。并且，依托SAP HAHA平台可以提供in-database分析。

<a href="http://www.bjt.name/wp-content/uploads/2012/04/image3.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-style: initial; border-color: initial; border-image: initial; border-width: 0px;" title="image" src="http://www.bjt.name/wp-content/uploads/2012/04/image_thumb3.png" alt="image" width="402" height="331" border="0" /></a>


<h3>Teradata</h3>


Teradata提供了免费的 <a href="http://developer.teradata.com/applications/articles/in-database-analytics-with-teradata-r">teradataR</a> 包，用于在R环境下连接Teradata数据库、创建数据、条用in-database分析函数。
<ul>
	<li>避免了从Tetadata到R之间的数据移动，有效提高了数据运算性能；</li>
	<li>针对于大数据的分析任务，使用Teradata的强大并行计算的能力 ；</li>
	<li>允许在R控制台操作；</li>
	<li>将常用的执行任务嵌入到数据库中执行；</li>
	<li>R和TetadataR都是免费的；</li>
</ul>
<h3><a href="http://www.sybase.com/products/financialservicessolutions/rap-thetradingedition?htab=Overview&amp;vtab=Editions&amp;hid=79970&amp;vid=102506">Sybase RAP</a></h3>
Sybase RAP主要是针对于金融市场的实时分析，其中RAPStore组件提供了内置分析函数，包括时间序列分析函数、OLAP函数、R语言整合函数以及用户自定义函数，适用于大数据环境。

其调用R函数的机理如下：

<a href="http://www.bjt.name/wp-content/uploads/2012/04/image4.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="image" src="http://www.bjt.name/wp-content/uploads/2012/04/image_thumb4.png" alt="image" width="541" height="221" border="0" /></a>

同时，还可以在R语言环境下通过RJDBC访问Sybase RAP，进行数据预处理，避免在R中数据清洗占用大量内存。

<a href="http://www.bjt.name/wp-content/uploads/2012/04/image5.png"><img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="image" src="http://www.bjt.name/wp-content/uploads/2012/04/image_thumb5.png" alt="image" width="543" height="159" border="0" /></a>

全文完，请期待R + Hadoop&gt;
