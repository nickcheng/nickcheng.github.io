---
date: 2007-02-02 00:46:09
type: post
title_en: 2007-02-02-public-the-ip-public
title: 发布内网机器的公网IP
wordpress_id: 334
tags:
- tech
---

家里的三台机器是用路由器组的局域网. 最近我需要把自己的机器配置成公网可以访问的服务器, 所以就在路由器的设置里把机器的IP放到了DMZ里. 这样, 我的机器就直接暴露在公网上了, 也就是说我本地配置的服务器通过公网IP可以直接访问了:)

不过因为是ADSL拨号上网, 所以如果路由器重新拨号, 那么公网IP就会发生改变, 这样就很不爽了! 所以为了解决公网IP改变的问题, 我写了一个Python小程序:)

	#coding=utf-8
	import urllib
	import re
	import libgmail
	import time
	
	# Get the page content
	url = 'http://username:password@192.168.0.1/status.htm'
	data = urllib.urlopen(url)
	pageContent = data.read()
	
	# Filter & Get the IP
	begin = pageContent.find('IP 地址', 3000)+21
	end = pageContent.find('&', begin)
	IP = pageContent[begin: end - 1]
	
	# Get current time
	t = time.localtime()
	datetime = "-".join([str(a) for a in t[:3]]) + ' ' + ":".join([str(a) for a in t[3:6]])
	
	# Generate content
	content = IP + ' - ' + datetime
	
	# Send mail
	ga = libgmail.GmailAccount("gmail帐号", "gmail密码")
	gcm = libgmail.GmailComposedMessage('nick.nickcheng@gmail.com', 'HOME IP', content)
	ga.login()
	ga.sendMessage(gcm)
	
	print "Done!"

这个程序的作用就是从路由器的管理界面取得当前的公网IP, 然后发邮件告诉我IP是什么. 有了这个程序以后, 再结合Windows的计划任务, 每半小时执行一次. 这样如果我的机器的IP地址发生了改变, 那么最长半小时时间后, 我就会在邮件中收到最新的IP地址:)

上面的程序用到了[libgmail](http://libgmail.sourceforge.net/)这个开源的python模块, 用他来调用Gmail的邮件功能非常的方便:) 具体可以看我的代码!

下一步的计划是把自己的一个子域名绑定到这个IP上, 如果IP发生了改变, 让程序自己去更改这个绑定!
