---
date: 2006-07-27 17:23:47
type: post
title_en: a-tool-to-get-the-source-of-metacafe-video
title: 获取Metacafe视频文件的小工具
wordpress_id: 280
tags:
- tech
---

昨天又发现一个类似Youtube的网站[Metacafe](http://www.metacafe.com). 这上面也有一些有趣的视频. 刚好昨天没太多的事情, 就顺手写了一个程序来抓[Metacafe](http://www.metacafe.com)上的视频的源文件:)

原理很简单, 就是去GET指定地址的HTML, 然后分析返回的原始代码! 中间辅用抓包工具简单分析了一下来往的HTTP包.

[下载地址](http://nblove.org/downloads/lab/Test.BackgroundWorker.zip)
运行程序需要.net framework 2.0, [微软官方下载地址](http://download.microsoft.com/download/2/3/c/23c4dddd-e32c-45de-9fcc-e6e906e2b429/dotnetfx.exe)

大家有兴趣的试试吧:) 有问题可以留言

ps. 有时间可能还会更新这个工具, 比如增加一些其他站点的下载:)

Get the source url from http://www.metacafe.com
[>>Download< <](http://nblove.org/downloads/lab/Test.BackgroundWorker.zip)
.net framework 2.0 required. [Download from microsoft](http://download.microsoft.com/download/2/3/c/23c4dddd-e32c-45de-9fcc-e6e906e2b429/dotnetfx.exe)
