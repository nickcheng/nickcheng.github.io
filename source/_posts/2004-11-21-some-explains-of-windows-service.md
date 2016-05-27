---
date: 2004-11-21 17:40:00
type: post
title_en: some-explains-of-windows-service
title: Windows服务的一些解释
wordpress_id: 95
tags:
- tech
---

alerter -错误警报器，垃圾  
  
application layer gateway service -给与第三者网络共享/防火墙支持的服务，有些防火墙/网络共享软件需要。占用　１。５ｍｂ内存。  
  
application management-用于设定，发布和删除软件服务。  
  
automatic updates -windows自动更新，靠，滚！  
  
background intelligent transfer service -这个服务原是用来实现http1.1服务器之间的信息传输，微软称支持windows更新时断点续传  
  
clipbook - 用与局域网电脑来共享 粘贴/剪贴的内容。（靠，想得出！）  
  
com+Event system　-一些 COM+　软件需要，检查你的 c:\program files\ComPlus Applications 目录，没东西可以把这个服务关闭．  
  
COM+Event system application　－同上  
  
COmputer browser　－　用来浏览局域网电脑的服务，但关了也不影响浏览！垃圾  
  
cryptographic services -windows更新时用来确认windows 文件指纹的，我更新时才开启一下。  
  
DHCP client－静态ＩＰ者需要（ｘＤＳＬ　等）小猫就不用了！！  
  
Distributed link tracking client－用于局域网更新连接信息，比如在电脑Ａ有个文件，在Ｂ做了个连接，如果文件移动了，这个服务将会  
  
更新信息。占用４兆内存。  
  
Distributed Transaction coordinator－无聊的东西。  
  
DNS Client－ＤＮＳ解析服务。。无聊～～  
  
Error reporting service -错误报告器，把windows中错误报告给微软，无聊～～～～～  
  
＊Event Log - 系统日志纪录服务，很有用于查找系统毛病．  
  
Fast user switching compatibility－多用户快速切换服务．．无聊  
  
help and support -帮助，无聊，还是无聊帮助．．哈哈  
  
Human interface device access－支持＂弱智“电脑配件的。。比如键盘上调音量的按钮等等。。  
  
IMAPI CD-burning COM service　－ｘｐ刻牒服务，用软件就不用了，占用１。６兆内存。  
  
Indexing service -恐怖的xp减速的东东！！！关关关！！！  
  
Internet Connection Firewall(ICF).........-xp防火墙。。不用就关。  
  
IPSEC Services－大众用户连边都沾不上。  
  
Logical Disk manager　－磁盘管理服务。。需要时它会通知你，所以一般关。  
  
Logical Disk manager administrative service－同上。  
  
messenger -不是msn，不想被骚扰的话就关。注：妖刺就是利用这个。  
  
MS software shadow copy provider－无用，据说是备份用的。。我看什么用都没。  
  
Net Logon－登陆　Ｄｏｍａｉｎ　Ｃｏｎｔｒｏｌｌｅｒ　用的，大众用户快关！  
  
Netmeeting remote desktop sharing－用ｎｅｔｍｅｅｔｉｎｇ　实现电脑共享。。晕！关！！  
  
Network Connections - 上网／局域网要用的东东！  
  
Network DDE　－和ｃｌｉｐｂｏｏｋ一起用的，无聊～～～～  
  
Network DDE DSDM　－同上  
  
Network Location Awareness－如有网络共享或ICS/ICF可能需要.(服务器端）  
  
NT LM Security support provider－telnet　服务用的东东，关！！  
  
NVIDIA Driver Helper service -nvidia 显卡帮助，关！  
  
PDEngine - perfectdisk 引擎  
  
PDScheduler -perfectdisk 计划服务  
  
PerFORMance logs and alerts－记录机器运行状况而且定时写入日志或发警告，内容可能过于专业，所以。。自己决定。  
  
＊Plug and Play - 自动查测新装硬件，即插即用，开着吧～～～  
  
Portable media serial number－绝对无用，无聊之及。  
  
Print Spooler -打印机用的，我打印时才开一下。  
  
Protected Storage－储存本地密码和网上服务密码的服务，包括填表时的“自动完成”功能。  
  
QoS RSVP -关！就是那个２０％的　ＱｏＳ  
  
Remote access auto connection manager－宽带者／网络共享可能需要！！  
  
Remote desktop help session manager－远程帮助服务，傻透，占用４兆内存。  
  
＊Remote Procedure Call (RPC) -系统核心服务！  
  
Remote Procedure Call LOCATOR－这个倒没什么用，管理　ＲＰＣ　数据库服务，占用１兆内存。  
  
remote registry －远程注册表运行／修改。大漏洞，还不快关！！  
  
removable storage　－一般情况下不用，磁带备份用的。  
  
routing and remote access－哈哈。。不知者关！  
  
secondary logon－给与administrator 以外的用户分配指定操作权．晕～～～  
  
security accounts manager－像 Protected Storage,　IIS Admin 才需要。  
  
server -局域网文件／打印共享需要的。  
  
shell hardware detection－给有些配置自动启动，像内存棒，和有些ｃｄ驱动等  
  
smart card -关！１。４兆内存  
  
smart card helper -关！  
  
SSDP Discovery service－没有什么硬件利用这个服务。。  
  
system event notification－记录用户登录／注销／重起／关机信息。。谁管这些。。  
  
system restore service -系统还原服务，吃资源和内存的怪兽。。虽然有时用到，自己决定。  
  
task scheduler－windows 计划服务啦，垃圾．  
  
TCP/IP NetBIOS helper－如果你的网络不用　Netbios 或WINS，关了．  
  
Telephony - 拨号服务，如果你的宽带不用拨号，那么关了它。  
  
telnet -大漏洞，我第一个关的就是这个．这根dos中　ｔｅｌｎｅｔ　命令没关系。２兆内存。  
  
terminal services－实现远程登录本地电脑，快速用户切换和远程桌面功能需要，不用这些功能就关了吧。  
  
themes -给ｘｐ打扮的东东，不要太花锹的就关了。  
  
uninterruptible power supply－停电保护设备用的。。。没有的就关。  
  
universal plug and play device host－同SSDP Discovery Service ，没用．  
  
upload manager－用来实现服务器和客户端输送文件的服务，简单文件传输不需要这个！  
  
volume shadow copy－同MS Software Shadow Copy Provider，无用．  
  
webclient－可能和以后的．ｎｅｔ技术有联系，安全起见，我关得实实的！  
  
＊Windows Audio -　控制着你听到的声音。关了就没声音了！！  
  
Windows Installer -windows的ＭＳＩ安装服务，建议设成手动。  
  
windows image acquisition (WIA) -有些数码相机和扫描器用的，我的扫描器觉得它没用。  
  
＊Windows Management Instrumentation - 满重要的服务，是管＂服务依靠＂的，但关了会出现奇怪的问题．  
  
windows management instrumentation driver extensions－没上面的重要，建议设成手动．  
  
windows time -网上时间校对．．晕  
  
wireless zero configuration -无线网络设置服务．．很少人用吧．．．  
  
WMI perFORMance adapter -关！占用６兆内存．  
  
＊Workstation -很多服务都依靠这个服务，支持联网和打印／文件共享的．
