--- 
layout: post
title: "生活在云的世界里"
tags: 
- dropbox
- google
status: publish
type: post
published: true
---
这是一篇凑数博客，囧～

很多人都是办公电脑和私人电脑各一台，很多时候需要同步在两地的数据，比如文件啊、标签啊、笔记啊啥的。
这时候云存储的应用就有用武之地了。下面介绍一下我常用的三款数据同步应用。


# evernote
这款产品适用于电脑、手机、网页间的笔记同步，是一款收集碎片知识的利器。什么信息都可以向上丢，
得空有整片时间则整理这些知识，形成笔记。比如在办公场所看到一篇不错的技术博客，但当时又没时间精读，
就可以将博客内容拷贝至evernote中，待回家之后，打开相同帐号的evernote，继续阅读提炼所需信息。

# Google Chrome
把它拿出来，主要是由于Chrome有evernote的插件，支持一键剪辑（文字）片段，文章，url。如果是剪辑文章的话，
会自动根据排好版式。比如排版非常恶心的r-blogger，左边栏的内容根本一点用没有。
用这个功能一键就舒服地把标准话的正文传到云端（有kindle的童鞋用这个功能可以省掉很多麻烦噢）。
Chrome还有个功能就是可以同步书签，不论在哪里，Google帐号登录以后，标签全部同步，该有的全有了，非常方便。

# Dropbox
这款产品就更NB了，可以同步文件。比如办公和私人电脑都安装了Dropbox应用，设置一下location文件夹，
那不论你在哪台机器上变更了文件，在另一台也会有相同的变化。像我的话，办公电脑U口被封，又不喜欢邮件来邮件去（太麻烦），那所有的文件交换就全靠它。

用这个应用还有一个好处，就是做R扩展包的同步。在R的etc目录下Rprofile.site文件中增加如下语句：


    .Library.site &lt;- file.path("D:/Dropbox/site-library/")
    .libPaths(.Library.site)


意思很明显，就是将所有的R扩展包装载`D:/Dropbox/site-library/`这个位置，不论哪台电脑上有包的变化，Dropbox都会做忠实的同步。
有人肯定会问，你`install.packages`又不麻烦，费劲巴力的这么搞这么一下干嘛？因为单位网关屏蔽了所有zip文件的入口，故不得已而为之～～

P.S 安装R包的时候记得Pause syncing
