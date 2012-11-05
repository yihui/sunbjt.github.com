--- 
layout: post
title: "n \xE8\xBF\x9E\xE7\x8E\xAF\xE7\x9A\x84\xE8\xA7\xA3\xE6\xB3\x95\xE4\xB8\x8E\xE5\xAE\x9E\xE9\x99\x85\xE6\xAD\xA5\xE9\xAA\xA4\xE6\x95\xB0"
tags: 
- algorithms
status: publish
type: post
published: true
category:
  - algorithms
meta: 
  _edit_last: "2"
  _wp_old_slug: n-%e8%bf%9e%e7%8e%af%e7%9a%84%e8%a7%a3%e6%b3%95%e4%b8%8e%e5%ae%9e%e9%99%85%e6%ad%a5%e9%aa%a4%e6%95%b0
  _efficient_related_posts: a:0:{}
  _relation_threshold: ""
  dsq_thread_id: "600836597"
---
九连环这个玩具，最早在高中的时候摸过，记得解它的时候因为很多重复步骤，所以恨不得要把它拆掉，还好最后解开了，不然我又得加条"亵渎古人智力"的罪名，呵呵。闲话少扯，下面是 n 连环实际步骤数的求法：
<pre lang='rsplus'>
gg <- function(n){
a <- numeric(n)
a[1] <- 1
a[2] <- 1
for(i in 3:n){
a[i] <- a[i-1] + 2*a[i-2] + 1
}
a}
</pre>

比如九连环的实际步骤：
<pre lang='rsplus'>
gg(9)
</pre>
[1]   1   1   4   7  16  31  64 127 256
