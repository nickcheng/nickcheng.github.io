---
date: 2008-01-02 22:12:00
type: post
title_en: the-trouble-of-vista-and-xp-installation
title: 搞定双启动, 先装Vista,后装XP的麻烦
wordpress_id: 426
tags:
- tech
- install
- start
- vista
- xp
---

家里电脑原来的系统又崩溃了, 我也跟着一起崩溃了...不过总不能不管啊, 于是又抖擞精神装了个新系统, 装系统的时候也不知道抽什么风, 竟然想装MacOS(估计觊觎苹果太久了), 结果当然是失败, 不过还好让我头脑清醒了一点儿; 之所以说一点儿, 是因为我又决定装Vista.

Vista安装的那是一个顺利, 好歹自己用了许久了, 但当我装完突然想到还有一个工程是在Vista没有试过的, 为了保证项目的运行, 我还得装一个XP...我都要无语了...咋整? 没辙, 再次抖擞装吧...

这次装完可好, Vista进不去了; 于是用Vista安装盘进入修复, 又好, XP又进不去了, TNND, 这儿跟我逗闷子呢...好在我还有两把刷子...

因为Vista已经不用boot.ini了, 所以先在Vista下用 bcdedit增加一个XP的启动项. 重启后进入XP, 发现系统提示找不到XP用的ntldr, 好说, 再用xp安装盘进入故障控制台, 从光盘的i386目录中把ntldr和ntdetect.com复制到xp安装盘根目录, 继续重启...

哦也, 我熟悉的XP回来了...记录一下吧, 我容易么?

ps. 上文省略了大量的失败过程, 失败的经验就不和你们分享了...
