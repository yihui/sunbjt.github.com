--- 
layout: post
title: "Oracle\xE6\x95\xB0\xE6\x8D\xAE\xE5\xBA\x93\xE5\xBC\x80\xE5\xA7\x8B\xE6\x94\xAF\xE6\x8C\x81R\xE8\xAF\xAD\xE8\xA8\x80"
tags: 
- datamining
- Oracle
status: publish
type: post
published: true
category:
  - R Computing
---
一则令人兴奋的简讯：

据<a href="http://blogs.oracle.com/" target="_blank">Oracle官方博客</a> 最近更新的 <a href="http://blogs.oracle.com/datamining/2010/05/new_r_interface_to_oracle_data_mining_available_for_download.html" target="_self">New R Interface to Oracle Data Mining Available for Download</a>，甲骨文开始正式支持R语言在Oracle数据库中的应用（简单的非官方说法是：甲骨文贡献了一个提供Oracle和R之间接口的附加包）。

援引博客中对R-ODM(R-Oracle Data Mining)的介绍：

R-ODM is especially useful for:
<ul>
	<li>Quick prototyping of vertical or domain-based applications where the Oracle Database supports the application</li>
	<li>Scripting of "production" data mining methodologies</li>
	<li>Customizing graphics of ODM data mining results (examples: <a href="http://www.oracle.com/technology/products/bi/odm/images/rodm_classification.jpg">classification</a>, <a href="http://www.oracle.com/technology/products/bi/odm/images/rodm_regression.jpg">regression</a>, <a href="http://www.oracle.com/technology/products/bi/odm/images/rodm_anomaly_detection.jpg">anomaly detection</a>)</li>
</ul>
众所周知，R在实现原型算法方面有着不可替代的巨大优势。诚然，通过R实现的一般性数据挖掘算法都可以嵌入到数据库中，但Oracle提供的这个接口，极大地提高了挖掘算法的部署效率。

今天（2010.06.08），<a href="http://cran.r-project.org/" target="_self">CRAN</a>上更新了<a href="http://cran.r-project.org/web/packages/RODM/index.html" target="_self">RODM</a>包的1.0-2版本，支持Windows、Linux、MacOS X系统。

下面是RODM包帮助文档中的一个例子，可以初步地体会算法高效的部署：
<pre lang="rsplus">### GLM Regression
## Not run:
x1 &lt;- 2 * runif(200)
noise &lt;- 3 * runif(200) - 1.5
y1 &lt;- 2 + 2*x1 + x1*x1 + noise
dataset &lt;- data.frame(x1, y1)
names(dataset) &lt;- c("X1", "Y1")
RODM_create_dbms_table(DB, "dataset")   # Push the training table to the database

glm &lt;- RODM_create_glm_model(database = DB,    # Create ODM GLM model
                             data_table_name = "dataset",
                             target_column_name = "Y1",
                             mining_function = "regression")

glm2 &lt;- RODM_apply_model(database = DB,    # Predict training data
                             data_table_name = "dataset",
                             model_name = "GLM_MODEL",
                             supplemental_cols = "X1")
windows(height=8, width=12)
plot(x1, y1, pch=20, col="blue")
points(x=glm2$model.apply.results[, "X1"],
       glm2$model.apply.results[, "PREDICTION"], pch=20, col="red")
legend(0.5, 9, legend = c("actual", "GLM regression"), pch = c(20, 20),
                col = c("blue", "red"),
                pt.bg =  c("blue", "red"), cex = 1.20, pt.cex=1.5, bty="n")

RODM_drop_model(DB, "GLM_MODEL")            # Drop the model
RODM_drop_dbms_table(DB, "dataset")   # Drop the database table
RODM_close_dbms_connection(DB)
RODM_close_dbms_connection(DB)</pre>
<blockquote>说一句题外话：
R的影响力除了在统计分析领域（SAS、SPSS、Statistica已经都开始支持R接口）外，已然发展到了商业数据库领域。</blockquote>
永久链接：http://bjt.cos.name/2010/06/oracle-data-mining-r/
