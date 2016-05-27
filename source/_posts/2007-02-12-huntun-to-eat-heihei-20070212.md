---
date: 2007-02-12 23:39:12
type: post
title_en: 2007-02-12-huntun-to-eat-heihei-20070212
title: 混沌志-20070212
wordpress_id: 338
tags:
- tech
---

分针刚跳

Droupnir的系统经过白天的折腾已经完成了基本的Update, 一共打了差不多70个补丁, 后来我还给他擦了半天屁股:(

虚机到一个稳定状态后, 在单位的服务器上做了一个备份. 说不定以后还会用到呢!

晚上回来继续给虚机装软件
	
* Python 2.5
* Apache 2.24
* Mod_Python 3.3.0b for Python 2.5
* Django 0.95.1(需要先装ez_setup.py)

软件装着不费劲, 关键是准备软件的时候费劲! 本想偷懒省劲从家里的电脑把这些软件复制过来, 可最后折腾了半天网络, 只完成了一半...最后还是把家里的电脑弄成了http server才把软件复制过来, 真他妈臭......

软件安装的顺序就是上面我写的顺序, 装好以后做个小实验, 看看django是否能work. 最后再配置apache就ok了!

具体参考我的文章: [http://wiki.woodpecker.org.cn/moin/nickcheng/2007-02-06](http://wiki.woodpecker.org.cn/moin/nickcheng/2007-02-06)

明天要搞数据库!!

考虑了一下, Trac&SVN就不在这个虚机里装了! 配置管理和开发环境的稳定程度可不能同日而语, 还是分开保险一些:)
