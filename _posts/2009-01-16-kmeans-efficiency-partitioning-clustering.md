--- 
layout: post
title: "K means"
tags: 
- "算法"
status: publish
type: post
published: true

---
Hierachial clustering 这类的方法最大的问题就在于对计算机内存的占用，当然对计算量也是一个严重的考验。n×m  的矩阵要进行 n×n 次计算，
n^2 这个函数估计大家应该记得很清楚，汗~~~~

Partitioning clustering 好处就是将计算量由 x^2 变为 x ，即线性函数。而其典型代表就是kmeans：

<a href="http://axqpza.bay.livefilestore.com/y1pXAqCw0JTJPPkFHsiN1_HZbucvbdhpjM3X6lE0cZYS3YRvglj1w8NXRpuQHtNFbXvf2cStsCd9iih286zTxiABA?PARTNER=WRITER"><img style="border-top-width:0px;display:inline;border-left-width:0px;border-bottom-width:0px;border-right-width:0px" title="kk" src="http://axqpza.bay.livefilestore.com/y1pz8-4sUNe2IVHTdInvQYO0NCCQdWba_swnqUrl_SBjZXku_XroELug4NWUzd2S54X5JWPDt4F8CQQMuCq4SJIBQ?PARTNER=WRITER" border="0" alt="kk" width="593" height="327" /></a>

图一是kmeans 算法中，增加变量（由1到100）的运算时间，图二是增加单维变量长度（x×1到x×100）。如果增加变量情形下，估计HC应该和PC 一致，但如果同时增加case的话，HC必然崩溃……
