---
date: 2008-02-26 09:51:03
type: post
title_en: 2008-02-26-adjust-vista
title: 调校Vista
wordpress_id: 428
tags:
- tech
- tuning
- vista
---

早上在[西行资讯](http://www.appbeta.com/)看到[一篇Vista调校的文章](http://www.appbeta.com/50226711/aecvistaieae_139767.php), 说的都是我还不知道的方法, 感觉很有用, 于是摘来备用:)

**1、UAC**：其实，对付UAC不仅仅是关闭一种方法，除了开启全功能UAC、关闭UAC外，我们还可以即开启UAC（利用其安全功能）又可以让其在"安静"模式下工作。我们需要借助[TweakUAC](http://www.tweak-uac.com/)工具，可以[点击这里下载](http://www.tweak-uac.com/TweakUAC.exe)。   
  
![](http://lh6.google.com/nick.nickcheng/R8NwfUA5_sI/AAAAAAAAAIY/doJt-Tk7T4k/TweakUAC-main-screen.jpg)   
  
  
**2、更快的磁盘性能**：仅针对SATA磁盘有效。再向磁盘写入前，Vista会使用内存作为高速缓存，风险就是突然断电会致使这部分数据丢失。   
  
![](http://lh4.google.com/nick.nickcheng/R8Nwf0A5_tI/AAAAAAAAAIg/kUr493KwYWM/vista_disk-performance.png)   
  
  
3、加速网络文件性能：可能是系统设计原因致使网络文件操作速度降低，可以使用管理员权限运行"cmd"，执行   
netsh int tcp set global autotuninglevel=disabled   
命令，[禁用Vista的"Auto Tuning"功能](http://www.techtree.com/India/Guides/Vista_Tips_n_Tricks/551-87086-584-1.html)，开启可以使用这个命令：   
netsh int tcp set global autotuninglevel=normal   
  
![](http://lh5.google.com/nick.nickcheng/R8NwgEA5_uI/AAAAAAAAAIo/i2hIkVVqtSQ/vista_network-copy.png)

   Technorati : [config](http://technorati.com/tag/config), [setup](http://technorati.com/tag/setup), [vista](http://technorati.com/tag/vista)
