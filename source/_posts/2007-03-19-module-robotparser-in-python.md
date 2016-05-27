---
date: 2007-03-19 22:10:32
type: post
title_en: 2007-03-19-module-robotparser-in-python
title: python的robotparser模块
wordpress_id: 348
tags:
- tech
---

读一个Python的爬虫代码的时候看到一个名字叫做"robotparser"的模块, 查了一下, 是用来解析网站的"robots.txt"文件的. 用法很简单, 举个例子

	rp = robotparser.RobotFileParser()
	rp.set_url("http://www.musi-cal.com/robots.txt")
	rp.read()
	rp.can_fetch("*", "http://www.musi-cal.com/cgi-bin/search?city=San+Francisco")  # return False
	rp.can_fetch("*", "http://www.musi-cal.com/")  # return True

程序很简单. 首先将类实例化, 然后用"set_url"方法设置"robots.txt"文件的路径, 这个文件一般都在网站的根目录. 接着调用"read"方法来解析这个文件. 最后就是用"can_fetch"方法来判断这个网站是否让你的程序(爬虫)访问某个网站内的链接了!

如果这个网站没有"robots.txt"文件的话, 在"read"方法后查看"rp.errcode"属性, 会看到404的返回值, 如果有这个文件就是200的返回值了!

相关链接

官方文档: [http://docs.python.org/lib/module-robotparser.html](http://docs.python.org/lib/module-robotparser.html)

一个家伙不满意自带的这个东东, 自己又写了一个: [http://nikitathespider.com/python/rerp/](http://nikitathespider.com/python/rerp/)

robots.txt规范: [http://www.robotstxt.org/wc/norobots.html](http://www.robotstxt.org/wc/norobots.html)
