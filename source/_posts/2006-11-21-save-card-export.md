---
date: 2006-11-21 12:58:06
type: post
title_en: save-card-export
title: CardExport复原了！
wordpress_id: 309
tags:
- life
---

![](http://mundogeek.net/wp-content/cardexport2.gif)

Card Export是一款很好用的Palm软件。他可以把Palm手机虚拟成U盘，这样不仅可以当做一个U盘，而且向卡里安装程序也变的方便了很多，只需要简单的copy一下就可以了！

不过，最近在我使用这个软件的时候，总在Palm上提示我“Cannot send USB descriptor. Host failure”这是怎么回事？由于没有头绪，只好Google。哈哈，网络就是好啊！已经有人成功的解决了这个问题，地址在这里：

<http://mundogeek.net/archivos/2006/03/12/card-export-ii-cannot-send-usb-descriptor-host-failure/>

大概的解决方法就是利用软件把Saved Preferences里的一条记录删除即可。我的文件管理工具是Filez，所以我简单说一下用Filez怎么操作。

打开Filez后，选择“View Preferences”，然后在左边的列表里找到“pusc”这条记录，然后删除即可！有的人碰到的情况是需要删除“pusb”这条记录，看看你能找到哪个吧。删了以后就好了！
