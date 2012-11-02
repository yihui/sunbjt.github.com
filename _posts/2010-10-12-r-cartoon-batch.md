--- 
layout: post
title: "R\xE4\xB9\x8B\xE4\xB8\x8D\xE5\x8A\xA1\xE6\xAD\xA3\xE4\xB8\x9A-\xE6\x89\xB9\xE5\xA4\x84\xE7\x90\x86\xE6\xBC\xAB\xE7\x94\xBB"
tags: 
- ImageMagick
- "\xE4\xB8\x8D\xE6\x97\xA0\xE6\xAD\xA3\xE4\xB8\x9A"
status: publish
type: post
published: true
category:
  - Z7Z8
meta: 
  _edit_last: "2"
  _efficient_related_posts: "a:1:{i:0;a:4:{s:2:\"ID\";s:5:\"10720\";s:10:\"post_title\";s:18:\"\xE9\x82\xA3\xE5\x8F\xAA\xE5\xA5\x94\xE8\xB7\x91\xE7\x9A\x84\xE9\xA9\xAC\";s:7:\"matches\";s:1:\"1\";s:9:\"permalink\";s:48:\"http://www.bjt.name/2011/11/running-horse-movie/\";}}"
  _relation_threshold: "1"
  dsq_thread_id: "600837423"
---
声明1：估计这篇博文的受众会很少很少……

声明2：请将下载的漫画于24小时内删除，balabala……

话说到，为了保护我已经不太好的视力，前几天购置了一台Kindle DX，用来阅读电脑上大量存在电脑中的的pdf格式电子书。这个东东确实比较强悍，除了对这些pdf文字书籍支持比较不错外（当然有些书籍需要进行一些处理），对pdf格式的漫画支持更赞。

而我是一个彻底的漫粉，闲暇之余，从网上下载jpg格式的漫画（推荐下载工具ComicAiII），悠然自得看漫画，实在惬意的很～～

不过，有些下载的漫画有些问题，比如下面的这种的：

<a href="http://www.bjt.name/wp-content/uploads/2010/10/Naruto_04_086.jpg"><img class="aligncenter size-full wp-image-10682" title="Naruto_04_086" src="http://www.bjt.name/wp-content/uploads/2010/10/Naruto_04_086.jpg" alt="" width="644" height="503" /></a>
<p style="text-align: left;">如果直接合并为pdf在Kindle DX上阅读，纵向显示的话，上下各有很大一块白边，画面非常小；
<a href="http://www.bjt.name/wp-content/uploads/2010/10/Naruto_04_086_1.jpg"><img class="aligncenter size-full wp-image-10682" style="border: 1px solid black;" title="Naruto_04_086_1" src="http://www.bjt.name/wp-content/uploads/2010/10/Naruto_04_086_1.jpg" alt="" width="430" height="630" /></a></p>
如果横向显示，效果更差，底部有一部分不能显示。想看完两页漫画的话，需要向上下翻页反复操作：
<a href="http://www.bjt.name/wp-content/uploads/2010/10/Naruto_04_086_2.jpg"><img class="aligncenter size-full wp-image-10682" style="border: 1px solid black;" title="Naruto_04_086_2" src="http://www.bjt.name/wp-content/uploads/2010/10/Naruto_04_086_2.jpg" alt="" width="644" height="503" /></a>

琢磨来琢磨去，还是得手动把漫画裁剪为适合Kindle阅读的大小（Kindle DX的标准9英寸屏显示区域和32开纸大小接近），并且把裁剪后的漫画顺序调换（日本漫画的阅读习惯是从左向右）。

说白了需要对每页jpg漫画做两件事：
<ul>
	<li>从中间分割，将一张jpg图片变为两张；</li>
	<li>为左右两张子图的增加顺序标记。</li>
</ul>
如果将分割的两张图片，右边图增加_0，左边图增加_1，即可满足要求。拿上面的086.jpg举例：170页（即右边部分）会被命名为086_0.jpg，171页会被命名为086_1.jpg，由于有了0、1标记，这样所有更新过的jpg合并为pdf文件的话，即可保证顺序的正确。

这一过程使用<a href="http://www.imagemagick.technocozy.com/" target="_blank">ImageMagick</a>和<a href="http://www.r-project.org" target="_blank">R</a>来实现(Windows XP平台)：

假如你的火影忍者的目录为D:/漫画/Naruto04，文件为001.jpg、002.jpg……，
<pre lang="rsplus">setwd("D:/漫画/Naruto04")
dd &lt;- dir()
ff &lt;- function(x){
    convert &lt;- paste("convert " , x ,
                     " -crop 2x1@ +repage +adjoin ",
                     "%d_",substr(x,1,3),".jpg",sep = '')
    shell(convert)
    reverse0 &lt;- paste("convert " , "0_", x ,
                      " ", substr(x,1,3), "_1.jpg", sep = '')
    reverse1 &lt;- paste("convert " , "1_", x ,
                      " ", substr(x,1,3), "_0.jpg", sep = '')
    shell(reverse0)
    shell(reverse1)
    shell(paste("del " ,"0_", x , sep = ''))
    shell(paste("del " ,"1_", x , sep = ''))
    shell(paste("del " , x , sep = ''))
}

for (j in dd) ff(j)
shell(paste('convert *.jpg ', '1.pdf',sep = ''))
</pre>
<pre>注意：目标文件夹的所有文件将被替换！</pre>
最后要强调的是，虽然Kindle没有辐射，和一般的纸质书区别不大，但看多了仍然有损视力 ^_^
