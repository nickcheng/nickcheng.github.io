---
date: 2006-03-19 01:47:39
type: post
title_en: the-fucking-trojen-and-the-spam-software
title: 这世道,垃圾和木马都让人恶心
wordpress_id: 241
tags:
- life
---

![](http://web.mit.edu/jpnet/ji/gifs/200x200/3364.gif)

之前写过一篇[关于那个winstall.exe的木马的post](http://nickcheng.com/index.php/2006/02/18/tmd-the-trojan/), 当时以为已经搞定了这个该死的东西, 可是谁知道, 那只是治标不治本! 后来的日子里, 还是总会在任务栏托盘处弹出该死的提示. 而且频率很高, 最少一天一次.

按照之前的处理方法, 先到C:\下一看, 果然出现了一个winstall.exe的可执行文件. 删除之, 提示消失. 可过一段时间, 那个该死的提示还会出现, C:\下的那个文件又出现了! 看来不能只盯着这儿了!

为了抓到是谁生成的winstall.exe文件, 我每天打开电脑都时, 都会打开[filemon](http://www.sysinternals.com/Utilities/Filemon.html)来记录各个进程处理文件的操作日志. 这可真痛苦, 也不知道他什么时候会出现, 只能这么等着, 而且有时还忘了开filemon...

终于, 今晚被我逮了个正着! 打开filemon的日志一看, 看到了一番奇特的景象.

还没有看到winstall.exe的时候, 看到了在我C:\Program Files\下, 有一个叫做"Daily Weather Forecast"的目录, 里面有一个weather.exe文件. 我可是从没有装过什么和天气预报相关的软件.

再一看, 这个进程在我档案的临时目录(temp)里建立了一个叫做539.exe的可执行文件. 这一切发生的时间, 正是系统弹出那个该死提示的时间!

(在此犯了一个错误, 在没有查到winstall的日志的时候, 我手误把日志清除了......)

再在系统进程中查看, 正有一个weather的进程在跑. 于是, 杀进程, 删目录(C:\Program Files\Daily Weather Forecast).

因为只是怀疑和这个东西有关, 所以还需要观察. 有后续我会继续写的! 大家都是疾恶如仇的!

处理完这个该死的东西, 我随手启动起来Autoruns([http://www.sysinternals.com](http://www.sysinternals.com))来查看系统的启动进程这些东西. 不幸, 又让我看到了两个恶心的东西.

注册表项 HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run 中有一个mscfs的启动项, 地址是c:\windows\system32\msibm\cfsys.dll. 这个是什么? 怎么没有听说过?? 赶紧Google了一下, 看到了一些信息:

[http://www.mhcnt.sh.cn/blog/blogview.asp?logID=300](http://www.mhcnt.sh.cn/blog/blogview.asp?logID=300) (此乃他人文章, 在此给出link, 详情请自行查看)

简单说, 这就是一个木马, 会干什么事情不是太清除, 但不会干什么好事情是肯定的了! 于是乎, 删注册表项, 删程序! 删程序的时候发现那个目录里的文件还挺多, 而且还有一个uninstall, 执行了一下, 还管用了, 不过还是残留了一些垃圾. 另外看到里面的web文件夹中有一些html格式的广告文件, 看了几个, 都是和游戏有关的! 看来这个软件也是国内的了:( 这帮只顾赚钱, 没有人品的家伙...

同时在system32目录下还看到了一个叫msicn的目录, 凭直觉, 我觉得这也不是什么好鸟! 进去一看, 嗬, 俨然一套应用程序, 还带一个plugin目录. TMD, 有见过装应用程序装到c:\windows\system32下的么? KAO, 让这写程序的昧良心的去死吧! 都是什么东西!

更可气的是这东西直接删还搞不定! 我又用上[Unlocker](http://www.softpedia.com/get/System/System-Miscellaneous/Unlocker.shtml), 才勉强删掉了这个东西!

在autoruns中继续看, 一个叫spoolsv的启动项赫然在目, 后面还写着"广州傲讯信息科技有限公司". 丫是干嘛的? 从来没听说! 而且叫这么一个名字, 不是图谋不轨是干嘛?(spoolsv是系统后台打印服务的名称) 一看目录, 好家伙, 系统的spoolsv在c:\windows\system32下, 丫的程序在c:\windows\system32\spoolsv下. 我说这公司就是TMD犯贱, 顺手Google了一下, 发现了更贱的事情!

原来这个SB吃屎公司杰作除了这个以外, 还有就是上面两个垃圾! (参见 [http://blog.diy0768.com/blogview.asp?logID=72](http://blog.diy0768.com/blogview.asp?logID=72))

大家在清理这几个东西的时候一定要注意清理完以后再看看, 我发现他们之间似乎会相互照应, 所以删的一定要彻底! 如果有什么问题可以给我mail: [nick.nickcheng@gmail.com](mailto:nick.nickcheng@gmail.com)

ps. 清理的时候又看到了另外的垃圾"中搜", 也是一家极为令人恶心的公司和手段, 之前写过文章说这个事情, 在此就不再赘述了. 不过如果让我再发现, 我还是会说的! 这次中搜中招应该是我表弟来上网时误装的!
