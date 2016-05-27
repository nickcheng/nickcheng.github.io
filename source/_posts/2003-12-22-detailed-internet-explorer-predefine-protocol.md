---
date: 2003-12-22 18:28:00
type: post
title_en: detailed-internet-explorer-predefine-protocol
title: 详解 Internet Explorer 的预定义协议
wordpress_id: 57
tags:
- tech
---

大家都知道，我们在使用IE浏览器的时候，经常在地址框中输入类似“http://xxx.xxx.xxx”的信息来浏览网页（http可以省略）。那为什么要在地址的前面输入“http”呢？  
  
稍有些互联网知识的朋友都知道，“http”含义就是“超文本传输协议”（Hypertext　Tranfer　Protocol）。IE浏览器就是通过超文本传输协议（HTTP），将Web服务器上站点中的网页源代码提取出来，并变成我们看到的漂亮的网页。  
  
还有些朋友也许也用过“ftp”。在地址框中输入“ftp://xxx.xxx.xxx”，我们就可以进入到互联网上的一些主机中（必须是已设置的），来下载或者上传文件。这里的“ftp”也是一种协议，它叫做“文件传输协议”（File Transfer Protocol）。使用它，我们可以很方便的在网络上传输文件。  
  
“http”和“ftp”是我们常用的两个协议，他们就是我们今天所说的“预定义协议”中的两员大将！除此之外，预定义协议还有其他的重要成员！下面我就为大家一一讲解：  
  
1、file协议  
  
他的作用是在本地或者网络上的一台计算机打开一个文件。  
  
使用方法：file:///盘符[|文件]  
  
文件要包含完整的路径名！比如我要通过IE浏览器打开自己电脑上C盘的“My Documents”目录，那么我只需要在浏览器的地址栏中输入“file:///C|/My Documents/”即可。如果习惯DOS下的输入方式，也可以使用“file:///C:\My Documents\”，甚至可以使用“file:///C:/My Documents/”。这就要看您的个人习惯了。这一招在网吧里有时也可以作为突破网管软件的一招^_^  
  
p.s. “file:///”可以省略  
  
2、gopher协议  
  
使用这个协议可以让你进入一个Gopher服务器，这种服务器提供的是一种目录系统。不过现在有了方便的World Wide Web，已经很少有人使用这个东东了，那我就不多说了。  
  
使用方法：gopher://Gopher服务器主机地址  
  
3、https协议  
  
这个协议的全称是Hypertext Transfer Protocol Secure，安全超文本传输协议。它最早是Netscape开发的，用于在网上需要保密的场合，比如网上交易时。  
  
使用方法：https://主机地址  
  
例如：https://example.microsoft.com
  
4、javascript协议  
  
这个协议可以让使用者在地址栏中运行一条Javascript语句。  
  
使用方法：javascript:Javascript语句  
  
有的时候我们也许会临时需要执行一条Javascript语句，这个时候他就派上了用场！  
  
例如：javascript:alert('JavaScript Link!');  
  
5、mailto协议  
  
使用系统默认的邮件服务软件来发邮件。  
  
使用方法：mailto:邮件地址[可选项]  
  
邮件地址就不用解释了，要注意多个地址要用逗号隔开，这里解释一下后面的那个“可选项”。第一个可选项必须加上前缀“?”，每两个可选项中间用“&”连接。可选项有：  
  
>subject：邮件的主题  
body：邮件的正文  
CC：抄送地址  
BCC：密件抄送地址  
  
我们举个例子，看看具体怎么使用。
  
	mailto:aaa@bbb.ccc?cc=aa@bb.cc&bcc=abc@bbb.ccc&subject=This is only a test  

在浏览器的地址栏中输入如上的命令以后，系统会自动调用默认邮件程序，并且自动建立一封新邮件。这时邮件的标题就是“This is only a test”；收信人地址是“aaa@bbb.ccc”；抄送地址是“aa@bb.cc”；密送地址是“abc@bbb.ccc”。  
  
6、news协议  
  
和mailto协议有些类似。他是使用系统默认的新闻组软件来打开一个新闻组  
  
使用方法：news:新闻组服务器地址  
  
例如：news:comp.databases.ms-sqlserver  
  
7、res协议  
  
这个协议一般都在IE WebControl控件中使用，我们平时可以说是根本用不到，所以就不说了（其实我也不知道^_^），大家知道有这么个东西就成了！  
  
8、telnet协议  
  
使用默认的远程登录软件登录到远端服务器。  
  
使用方法：telnet://服务器地址[:端口]  
  
例如：telnet://microsoft.com:4201  
  
9、view-source协议  
  
用默认的超文本编辑器打开一个位于远端服务器上的一个超文本文件。  
  
使用方法：view-source:地址  
  
这一招有一个好用处，就是在一个网页禁止查看源文件的时候，我们就可以使用这个方法来突破他的限制来查看源文件。  
  
例如：view-source:[HTTP://www.microsoft.com/default.asp](http://www.microsoft.com/default.asp)  
  
以上就是IE所包括的所有预定义协议，这些协议在IE4.0以上版本都可以使用！  
  
要注意一些问题  
  
1. URL中要用%20来代替空格，%23来代替“#”  
2. 有的情况下协议说明是可以省略的。比如你的地址是“www.xxx.xxx”这样的，浏览器会自动当作“http”处理；“ftp.xxx.xxx”会自动处理成“ftp://ftp.xxx.xxx”。“news”也是这样！而“file”就可以直接省略了！！  
3. 本文的例子均需要在浏览器的地址栏中输入。
