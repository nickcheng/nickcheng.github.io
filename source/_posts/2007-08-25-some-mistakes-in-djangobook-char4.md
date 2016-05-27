---
date: 2007-08-25 10:32:57
type: post
title_en: 2007-08-25-some-mistakes-in-djangobook-char4
title: djangobook 第四章中的遗漏
wordpress_id: 384
tags:
- tech
- book
- django
---

在建立模板对象(Creating template objects)这一小节中, 会让读者在解释器下简单试用一下基本函数, 但是这里讲的太简单的, 如果没有对环境进行很好的设置的话, 这几句简单的试用语句是会出错的!

解决方法是要增加两个Windows的环境变量:

	PYTHONPATH = c:\temp
	DJANGO_SETTINGS_MODULE = mysite.settings 

这里假定我是在 c:\temp 目录下执行的 django-admin.py startproject mysite 来建立的我的工程

[这里有有关这个问题的一个讨论(英文)](http://groups.google.com/group/django-users/browse_thread/thread/d732e9ca214b38d3)

