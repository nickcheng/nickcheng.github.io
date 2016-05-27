---
date: 2014-4-20 15:53
title: Apple TV 2 OS v6.1 使用自定义 DNS
title_en: use-custom-dns-in-appletv2-v61
tags:
- tech
- apple
- tv
- dns
- config
- youku
- sohu
- xunlei
- video
---

一直想把家里的 Apple TV2 重新启用给老婆看视频. 之前搞的时候一直没有找到合适的 DNS 地址, 今天偶然在 ip.cn 看到几个, 于是打算来试试看.

[Apple TV DNS 服务器 IP 地址](http://ip.cn/dns.html):

* 南方电信: 180.153.225.136
* 北方联通: 115.28.40.136	
* 香港: 111.68.8.179   	
* 国外: 182.16.230.98

一般来说, 按照上面设置好 Apple TV 的 DNS 以后, 返回主界面打开 "预告片", 就能看到 DNS 提供的内容了. 但是我却看到的是 "预告片不可用" 的提示字样.

网上搜了一圈, 原来是苹果全面启用了 HTTPS 的缘故导致. 现在需要先利用苹果的配置工具来给 Apple TV 刷个配置, 然后才能使用.

我在网上找到了教程和对应的文件, 有需要的可以自取, 按教程操作即可:

* [教程](http://nickcheng-blog.u.qiniudn.com/20140420/readme.pdf)
* [配置文件](http://nickcheng-blog.u.qiniudn.com/20140420/appletv-fix.mobileconfig)

参考链接:

* [【紧急更新】apple tv 3dns劫持被封解决方案：T大新版本ATV3劫持证书起死回生大法！](http://nasyun.com/thread-1825-1-1.html)
