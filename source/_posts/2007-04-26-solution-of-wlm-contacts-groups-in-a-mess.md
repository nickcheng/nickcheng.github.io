---
date: 2007-04-26 10:39:19
type: post
title_en: solution-of-wlm-contacts-groups-in-a-mess
title: WLM(俗称MSN Messenger)联系人混乱解决方法
wordpress_id: 358
tags:
- tech
- contact
- fix
- live
- messenger
- msn
---

开头先把名词明确一下, 本文的主角是WLM, 全称是Windows Live Messenger, 这是他的新名字(也不是太新了,嘿嘿). 他的老名字就是MSN Messenger, 也就是大家常说的MSN了.

然后把解决方案说一下, 因为我是Vista系统, 所以其他系统没有实验, 有需要的朋友可以参考我的解决过程:
	
1. 关闭WLM
2. 删除C:\Users\nickcheng\AppData\Local\Microsoft\Windows Live Contacts 目录下自己帐号对应的目录
3. 重新启动WLM, 登录之

搞定:)

最后是解决过程, 供大家参考:)

也不知道是自己人品实在太差还是WLM实在太烂, 某天我在使用WLM时, 突然感觉一闪, 瞬时间, WLM的联系人列表中的分组就变的乱七八糟了. 好友组里全是工作的同事, 同事组里全成了家里人, 我这个ft啊.

关闭WLM, 再启动之, 状况依然......TMD...真是点背啊... 当时因为有繁务缠身, 也没时间和他较劲. 好在WLM的搜索联系人功能还算好用.

不过这混乱的分组实在是看着碍眼, 今天早上一定要处理掉这个问题!

经过我一番缜密的思考(呵呵...), 想到了一个"手段", 嘿嘿...

根据经验, 这类大厂出品的软件不太会犯太过恶劣的过错, 也许这次联系人的混乱只是我本地的一次"抽筋". IM软件都会在本地机器中缓存一份联系人列表, 可能只是这缓存的列表出现了问题, 而在服务器那端, 我的分组信息应该还是正确的, 只不过我这边的软件还没有和服务器端同步. 如果是这样, 那我需要做的就是让我本地的联系人列表和服务器同步一下.

有了这样的想法, 就要看怎么能做到了. 自然, WLM不会提供一个按钮叫做"和服务器端同步"(这样的东东普通用户是无法理解滴), 所以就要想其他方法. 回想刚装新系统的时候, 机器里自然不会有什么缓存的联系人列表一说, 那时软件能做的只能是从服务器端去取用户的联系人列表. 哈哈, 这么一来, 我只需把本地缓存的联系人列表给清除掉, 然后再启动一次WLM就ok了.

说干就干, 先找本地联系人列表存放的地方.

这个好办, 祭起"[Procmon](http://www.microsoft.com/technet/sysinternals/default.mspx)"(查看运行中的程序访问了哪些本地路径的小工具, 这是Vista系统下用的, XP下叫Filemon), 然后启动WLM. 分析Procmon抓到的内容, 很容易就看到联系人列表存放的位置了:

	C:\Users\nickcheng\AppData\Local\Microsoft\Windows Live Contacts

剩下要做的就很简单了, 进入这个目录, 直接把你帐号对应的目录给干掉就好了! 再次登录WLM, 经过稍长时间的登录, 哈哈, 我的联系人分组又回来啦! 赞哦!
