---
date: 2004-11-06 05:04:00
type: post
title_en: about-authrities-of-aspnet-user
title: 关于ASPNET用户的权限
wordpress_id: 92
tags:
- tech
---

在ASP.NET下开发Web应用程序的时候, 尤其是和读写文件有关的情况下, 常常会发生ASPNET用户对某一个目录没有相应权限的问题, 这一点在NTFS分区中尤为明显.  
  
我们一般的解决方法就是在这个目录上点击右键, 然后在"属性"中选择"安全", 然后添加ASPNET用户到当前用户列表中.  
  
这样的方法固然可以, 不过如果有多个目录的话,就需要反复的操作, 显得繁琐了一些, 所以我们可以通过另一个方法来实现同样的效果, 而且更高效.  
  
我们可以在"管理工具"中, 选择"系统工具"-"本地用户和组"-"组", 双击"Administrator", 然后把ASPNET用户添加到组中. 这样一来, ASPNET用户就拥有了Administrator组的所有权限, 自然也就拥有了对所有目录的读写权限.  
  
不过使用这个方法前要考虑一下可能出现的安全问题和隐患:)
