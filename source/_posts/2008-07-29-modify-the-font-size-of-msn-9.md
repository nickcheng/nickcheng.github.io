---
date: 2008-07-29 18:21:00
type: post
title_en: 2008-07-29-modify-the-font-size-of-msn-9
title: msn 9.0 字体修改
wordpress_id: 436
tags:
- tech
- font
- hack
- live
- messenger
- msn
- reshack
---

从网站的统计中看到自己曾经的一篇[讲MSN字体修改的文章](http://nickcheng.com/2006/09/25/change-the-fontsize-of-msn-messenger/)很受欢迎. 也是, 那默认安装的MSN(现在叫Windows Live Messenger, 不过大家还是习惯叫MSN), 联系人列表的中文显示很是问题.

现在大家都用9.0很久了, 我也就再放一个9.0的修改好的文件供大家使用吧:)

下载地址: [http://www.box.net/shared/xkt2p7hoo4](http://www.box.net/shared/xkt2p7hoo4)

说明: 下载后的替换你的"c:Program FilesWindows LiveMessengermsgsres.dll"文件. 对应的MSN的版本是"Version 2009 (Build 9.0.1407.1107)", 英文版. 这个版本还把主界面的广告去了. 如果想知道怎么修改, 还请参考[原来的文章](http://nickcheng.com/2006/09/25/change-the-fontsize-of-msn-messenger/).

ps. 去广告的方法原文中没有, 在此给出来. 用ResHack打开msgsres.dll, 在4004-923中查找ID=Atom(SSConstrainer), 然后将前面的layoutpos=top改为layoutpos=none, 编译, 保存, 搞定!
