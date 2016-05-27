---
date: 2006-02-18 23:44:33
type: post
title_en: tmd-the-trojan
title: TMD, 中招了...
wordpress_id: 213
tags:
- tech
---

家里的机器, 没装防病毒软件, 也没有装防火墙. 果真就中招了!

一向以为只要自己使用电脑注意, 并且及时对操作系统进行更新, 就不会怎么中毒. 事实也差不多如此, 可是谁知道这两天还是让我中了一个, 不过还好, 是一个木马.

现象是这样. 最近使用电脑的时候, 右下角总是弹出一个"Your computer is infected..." 的提示框, 并且有一个红色的大叉. 还提示我点击下载防毒软件.  可我点了以后又没有什么反应. 一开始我还真的以为是操作系统检测到有问题才提示我的. 不过由于我这个人有些懒, 所以也就只是让它在那里显示着不管, 因为不碍我其他事, 而且运行其他程序也没什么问题, 我就一直没有在意, 准备找时间来收拾一下.

晚上回来,  想到这个问题, 于是开始google. 哈哈, 这下可好, 搜到的结果都是和木马有关的. 于是才意识到, 这原来是一个骗局! MMD, 跟老子过不去, 搞不死你!

这个病毒的名字叫: Trojan.Fakealert. 病毒描述是这样的:

By cheating as an anti-spyware installation file, and after it installs  malicious file on PC, it detects itself as a malicious code when it scans for  the infected PC ?To delete that malicious code, it requests user’s information  to make a payment to the user.

意思就是说, 他伪装成反病毒软件, 并在你系统里装了一个恶意程序. 然后假装告诉你说你中毒了, 需要下载软件来处理.

病毒的活动是这样的:

If Trojan.Fakealert(1) is executed for the first time, it makes its duplication  as follow into %root% folder.  

%root%\winstall.exe  

* Basic Windows root folder  (%root%)  

Windows 9X/ME: C:\  

Windows NT/2000 : C:\  

Windows XP : C:\

The  following message will be displayed. "Your computer has detected infection. It  is recommended to use antispyware tools to prevent data loss. Please click the  following link to protect your computer from sypwares."

It changes the  following registry to configure Desktop and configuration values of the infected  system.  [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\System  Wallpaper] "%systemroot%\desktop.html" * Basic Windows system  folder(%systemroot%) Windows 9X/ME: C:Windows\ Windows NT/2000 : C:Winnt\  Windows XP : C:Windows\ (the following is a deskptop.htm which is changed to  Desktop wallpaper.)  [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\ActiveDesktop]  NoChangingWallpaper = "dword:00000000" NoComponents = "dword:00000000"  NoAddingComponents = "dword:00000000" NoDeletingComponents = "dword:00000000"  NoEditingComponents = "dword:00000000" NoHTMLWallPaper = "dword:00000000"  [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer]  NoActiveDesktop = "dword:00000000" ClassicShell = "dword:00000000"  ForceActiveDesktopOn = "dword:00000001"

If Trojan.Fakealert(1) is executed, it  creates an icon on the system tray. "Your PC is infected by spyware. Click the  following link to protect your system."

When a user clicks on that icon, it  lead him/her to the sites where the user can download antispyware. 69. (omit) .  178 (80 port)

It adds the following registry values to execute itself whenever  Windows starts. [HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run] "Windows  installer" = "C:\winstall.exe" Alias: Trojan.Dropper

按这个说法, 他除了会在我的C:\下放一个名为winstall.exe的文件外, 还会在我的注册表写一些垃圾, 并且让我开机就自动运行. 而且在我点击他的提示的时候, 会带我去一个网站下东西.

可我并没有在注册表里找到东西, 也没有被连到某个网站, 不知道是不是这个病毒在我这里智障了, 呵呵...

不管了, 清理之! 方法很简单!

1. 在进程里, 杀掉winstall.exe  
2. 在C:\, 删除winstall.exe文件  
3. 在注册表中[HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run]位置清除自动启动项

好了, 搞定! 我还不准备装杀毒软件和防火墙, 再撑撑吧! 实在太懒^_^...
