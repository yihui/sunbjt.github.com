--- 
layout: post
title: "R\xE9\x95\x9C\xE5\x83\x8F\xE3\x80\x81SAS\xE3\x80\x81\xE5\x8F\x8AMySQL"
tags: 
- LaTeX
status: publish
type: post
published: true
category:
  - Information
---
前几天COS论坛上还在说中科大的R镜像还<a href="http://cos.name/cn/topic/104268" target="_blank">没弄好</a>，今天再看<a href="http://cran.r-project.org/mirrors.html" target="_blank">cran</a>，中科大的镜像已然可以正式使用。

中国的 R 语言镜像近几年来变化比较大，最早是东南大学，但不知道什么原因消失了。而后国内镜像主要集中在香港的geoexpat和厦门大学，再后来加入了中科院的两个所（包括CTeX），到今日加入中科大镜像。

个人一直觉得，人大作为中国R语言的倡导者，却一直没有提供镜像，挺遗憾的（人大文科氛围太浓烈）。

--------

关于SAS：

4月30日，dapangmao在 <a href="http://www.mysas.net/sns/index.php" target="_blank">SAS圈子</a> 更新了一篇博客——<a href="http://www.mysas.net/sns/space.php?uid=808&amp;do=blog&amp;id=853" target="_blank">SAS, 一个华丽时代的结束</a>，具体内容我就不在这里转了。不过有些奇怪的是，评论没有硝烟，不知道是因为SAS太封闭还是大家争累了。

------------

关于MySQL：

以前工作环境一般都是直接面对服务器上的Oracle、DB2，数据库安装、调试甚至数据源这些一般不用考虑。这两天项目需要，导了一些数据在本地。说来数据量也不大，1.5GB。一般的分析软件还不能直接搞定，于是乎倒腾上了MySQL。这个轻量级数据库挺有意思，注释和R是一样的（#），其前端工具heidisql不支持查询结果直接粘贴到word，却支持Copy selected rows as LaTeX table，大大的逗了我一下。以前我老说R和LaTeX是天然的搭档，现看来MySQL也是：）
