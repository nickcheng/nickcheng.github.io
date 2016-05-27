---
date: 2006-09-25 10:56:32
type: post
title_en: 2006-09-25-change-the-fontsize-of-msn-messenger
title: MSN字体修改
wordpress_id: 294
tags:
- tech
---

[msgsres.dll](http://www.box.net/lite/89bpkch0ig)

每次下到新版的MSN都要修改的一个东西就是联系人列表的字体的大小, 要不然中文的显示实在是难看之极! 修改方法如下:

使用ResHacker打开Messenger目录下的msgsres.dll文件, 具体目录应该在C:\Program Files\MSN Messenger\msgsres.dll
	
* 在4005->923->1033中寻找“sysmetric(-16)”, 把他改为“9pt”, 然后编译脚本
* 在4005->1004->1033和4005->1009->1033中寻找“FontSize:rcint(49615)pt;”, 把他改为“FontSize:9pt;”, 再次编译并保存, 搞定!

记得在修改之前备份你的文件:) 以防万一哦! 如果不会修改的, 可以直接下载我改好的文件, 替换你的文件! 我的MSN的版本是8.1.0068, 其他版本的我可不保证有效! 记得备份哦!

enjoy...^_^
