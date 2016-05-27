---
date: 2004-11-16 20:13:00
type: post
title_en: 2004-11-16-clear-up-some-trojen
title: 清除几个木马
wordpress_id: 93
tags:
- tech
---

今天回到家里上网, 刚打开Maxthon就弹出一个广告窗口, 这个问题已经好长时间了, 因为一直没时间, 所以也没有去整它. 刚好今天没事儿, 呵呵, 小木马, 你死定了!  
  
首先打开msconfig, 瓦赛, 这么多得启动项, 都是什么啊!  
  
winup.exe 这是什么东西? Google一下, 这可好, 原来是个象3721一样得烂东西, 不知道什么时候跑到我机器里了, 好! 废了他!  

> * 在IE的工具里点"管理加载项",禁用Downloadvalue Class , EyeOnIe Class ,URLMonitor Class  
* 在system32中运行一下henbangkiller.exe 再删除 winhtp.dll hap.dll xpieknl.dll winup.exe  
* 在注册表中删除HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run下的 winup 键HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run下的 updata键

这下他可不会再出来麻烦我了！  
  
不过我看到在msconfig里面还有一个可疑的东西：msstart.exe 不对吧，MS会弄一个这么个东东？系统都启动了，还来一个start？有问题！  
  
继续Google，哈哈，果然，这个也是个木马！杀之!  
  
先在任务管理器里干掉msstart的进程, 然后再到system32目录下delete掉msstart.exe这个文件, 看你再嚣张!  
  
不过我害怕还有不知道的木马, 所以现在我要去下一个Spy Sweeper查查我的机器
