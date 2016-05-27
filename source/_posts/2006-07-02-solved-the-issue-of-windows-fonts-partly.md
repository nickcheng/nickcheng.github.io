---
date: 2006-07-02 17:36:23
type: post
title_en: 2006-07-02-solved-the-issue-of-windows-fonts-partly
title: 部分解决Windows的字体问题
wordpress_id: 272
tags:
- tech
---

也不知道自己装了什么软件, 把系统的字体搞得有些乱！ 如果FeedDemon使用中文界面， 所有中文就会变成小问号！ Google Earth里的个人标注也都变成小方块！ 真是气煞我也！

先Google了一把， 找到一些头绪。 和自己之前在手机上整中文显示一样， Windows的字体和注册表有很大的关系！ 所以还是先从注册表入手！

打开RegMon， 然后启动FeedDemon。  这时再到RegMon中看刚才FeedDemon在启动的时候都访问了哪些注册表项！ 用“font”作为过滤条件， 一些注册表键值慢慢呈现出来！ 和注册表相关的就是“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\”下的“FontLink、FontMapper、Fonts、FontSubstitutes、GRE_Initialize” 这些项。

在此也懒得再试太多了，  我把朋友的电脑打开， 把他注册表中的这些项导出， 覆盖在我的注册表中， 然后重启电脑！ 呵呵， 貌似好了一些了！ Google Earth中的小方块不见了， 不过FeedDemon的问号还是健在， 有时偶尔能看到中文～～～看来拯救的还是不彻底啊～～～

目的基本达到， FeedDemon就用着英文的界面吧！  估计王道解决方案还是重装系统了-_-|||
