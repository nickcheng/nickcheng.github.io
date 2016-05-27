---
date: 2004-01-04 00:47:00
type: post
title_en: 2004-01-04-about-syntax-with-from-subsentence
title: 关于“FROM 子句语法错误”
wordpress_id: 66
tags:
- tech
---

前天调试一个asp.net下连接Access数据库的小程序,有这么一句总会出现"FROM 子句语法错误"的错误

`select * from user`

程序重写了n遍,数据库也重新建立了n遍,可是问题依旧...  
  
今天上网搜了一下,果真被我发现了解决方法和原因!  
  
原来,Access数据库中,"user"是一个关键字,所以这句话就会出现错误.解决的方法也很简单

`select * from [user]`

原来一切只是这么简单!

[](http://www.icbean.com/nickcheng/default.asp?cat=2)
