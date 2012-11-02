--- 
layout: post
title: "R\xE8\xAF\xAD\xE8\xA8\x80\xE7\x9A\x84\xE4\xBB\xA3\xE7\xA0\x81\xE8\xA7\x84\xE8\x8C\x83"
tags: 
- emacs
- google
status: publish
type: post
published: true
category:
  - R Computing
---
前些天在准备<a href="http://cos.name/chinar/chinar-2010/" target="_blank">中国第三届R语言会议（上海）</a>的时候，
翻到以前记录在Google Notebook里的一些材料，
一篇是关于Google Codes关于<a href="http://google-styleguide.googlecode.com/svn/trunk/google-r-style.html">R代码的规范</a>，非常值得借鉴。

规范这个东西平时多多注意一些还是有好处的，就和作文一样，漂亮的字体总能有不错的加分。这里就不翻译原文了，摘一些 tips 供大家参考：


### 1、一般性规则

<ul>
	<li>避免使用attach</li>
	<li>写函数是尽量少的使用stop()</li>
	<li>定义S3和S4的对象不要混在一起使用</li>
</ul>

### 2、文件命名

以.r结束的文件，尽可能的增加信息在文件名里面，比如

    Good:
    predict_ad_revenue.R
    
    Bad:
    foo.R

### 3、变量名和函数命名规则

注意，在R环境下，大小写是敏感的

变量：

    Good:               
    avg.clicks
              
    Bad:                
    avg_Clicks, avgClicks

函数名:

    Good:                                                                           
    CalculateAvgClicks                      
                                            
    Bad:                                                                            
    calculate_avg_clicks, calculateAvgClicks


### 4、字符间隔

这个可能是最快的，使代码外观变"漂亮"的规则了

    Good:
    tabPrior <- table(df[df$daysFromOpt < 0, "campaignid"])
                                                           
    Bad:
    tabPrior<-table(df[df$daysFromOpt<0,"campaignid"])     

这里包含了赋值、逻辑符号以及逗点分隔。

在R里面尽量少用 `=`

在函数里：

    Good:
    if (debug)

    Bad:
    if(debug)

### 5、代码组织
尤其是做项目的话，以下信息是必须有的：
<ol>
	<li>版权声明</li>
	<li>作者注释</li>
	<li>文件说明，项目目的，输入和输出的说明</li>
	<li><code>source()</code> 和 <code>library()</code> 说明</li>
	<li>函数定义</li>
	<li>其他</li>
</ol>

### 6、注释
养成良好的注释习惯
<ul>
	<li>单行注释以 # 开头，加一个空格</li>
	<li>短注释需要在代码后面空两格，然后 # ，再加一个空格</li>
</ul>
最后再一次推荐使用Emacs+ESS，虽然我已经折腾n多次了～～

永久链接：http://bjt.cos.name/2010/11/google-r-code-style
