---
date: 2007-10-16 17:06:00
type: post
title_en: the-tiny-difference-between-django-server-and-apache-server
title: Django server和Apache下运行Django的细微差别
wordpress_id: 401
tags:
- tech
- django
- error
- server
- url
- view
---

今天把在家调好的网站放到服务器上, 发现不能运行, 提示 ViewDoesNotExist 的异常错误. 一开始以为又是服务器上的文件访问权限问题, 但是 chmod 到 777 之后问题还是照旧, 而且在我本地用”manage.py runserver”运行还是没有问题. 于是乎, 去Python-Chinese的邮件列表寻找答案. 看到limodou有如下一说:

> 使用apache要复杂些，要把project的路径和它的父路径都加入sys.path中比较方便。而address.view的用法说明它是从project目录开始找的，所以要把project路径加入sys.path. 如果使用开发服务器，manage.py会自动将project的路径和它的父路径都加入sys.path中，而apache要自已来做。

这里已经说的很清楚了, 开发服务器的manage.py会在背后为你做一些事情, 而apache不会, 所以导致了我碰到的这个问题.

其实修改起来也很简单, 除了把路径加入sys.path之外, 还有一个方法就是在urls.py中, 把调用的方法名写成”项目名+模块名+方法名”的形式.

修改前代码: urls.py     

	from django.conf.urls.defaults import *
	
	urlpatterns = patterns('',
		(r'^$', 'view.index'),        
		(r'^s/$', 'view.search'),        
	)        

修改后代码: urls.py     

	from django.conf.urls.defaults import *
	
	urlpatterns = patterns('',       
		(r'^$', 'djangotest.view.index'),        
		(r'^s/$', 'djangotest.view.search'),        
	)
