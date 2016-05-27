---
date: 2007-01-23 21:44:08
type: post
title_en: build-django-site-on-bluehost
title: 在BlueHost上建立Django站点
wordpress_id: 329
tags:
- tech
---

主要参考了 [http://www.bluehostforum.com/showthread.php?t=715](http://www.bluehostforum.com/showthread.php?t=715) 这个帖子  

1. 事前准备

	安装SVN(BlueHost 默认是不支持SVN的, 需要自己安装) ,开通SSH(BlueHost里要想启用SSH, 竟然还需要身份证, 我ft...) , 并SSH上你的主机

	因为之前已经在BlueHost的主机上装好了SVN, 并且开通了SSH, 所以省了很多事情:)  

2. 获取Django代码

	在"~/"下建立"django_src"目录 
    
    	mkdir django_src

	进入目录 
    
    	cd django_src

	使用SVN获取代码 
    
    	svn co http://code.djangoproject.com/svn/django/trunk/ ./
    
3. 设置路径

	编辑".bash_profile"文件, 设置PYTHONPATH 和 PATH路径, 方便使用Django 
    
    	export PATH=$PATH:$HOME/django_src/django/bin
    	export PYTHONPATH=$PYTHONPATH:$HOME/django_src:$HOME/django_projects

	重新加载".bash_profile"文件, 来启用配置的路径 
    
    	source ~/.bash_profile

4. 建立项目目录

	在"~/"下建立"django_projects"目录 
    
    	mkdir django_projects

	进入目录 
    
    	cd django_projects

	建立Django项目"myproject" 
    
    	django-admin.py startproject myproject

	修改"myproject.settings"文件的权限, 限制只有你的用户可以读取, 这样可以避免同一个服务器上其他用户访问你的DB 
    
    	chmod 600 myproject/settings.py

5. 配置FastCGI

	这一步我花的时间最长! 关键是原文中的fcgi.py不能下载了, 我找了其他的fcgi.py又不对. 郁闷之下翻看了官方的文档, 官方文档说要用flup, 我又折腾了半天flup, 未果... 最后又Google了一堆fcgi.py, 终于被我找到一个对头的:)   

	现在BlueHost的控制面板里建立一个子域名(SubDomain), 建立成功后他会在你的"~/public_html"目录下建立对应的子域名的目录. 我建立了一个叫"lab"的子域名. 然后进入到这个目录中, 下载fcgi.py 
    
    	wget http://svn.saddi.com/py-lib/trunk/fcgi.py

	下载完毕后, 修改执行权限 
    
    	chmod 755 fcgi.py

	继续在这个目录下建立Django.fcgi, 文件内容如下 
    
    	#!/usr/bin/env python
    	import sys, os
    	sys.path.insert(0,"/home/username/django_src")
    	sys.path.insert(0,"/home/username/django_projects")
    	from fcgi import WSGIServer
    	os.environ['DJANGO_SETTINGS_MODULE'] = 'myproject.settings'
    	from django.core.handlers.wsgi import WSGIHandler
    	WSGIServer(WSGIHandler()).run()

	要注意, 上面的"username"需要改为你在BlueHost的用户名. "django_src"是最开始建立的放Django源代码的目录, "django_projects"是咱们建立的放项目的目录. 第6行的"myproject"是Django生成的项目的名字. 这几个一定要对应! 

	同样要修改执行权限, 这里再提醒一下大小写! 
    
    	chmod 755 Django.fcgi

6. 配置Rewrite Rule

	这个就简单了, 照葫芦画瓢! 和上面的Django.fcgi文件在同一个目录下, 建立.htaccess文件(别把点忘了), 内容如下 
    
    	RewriteEngine On
    	RewriteBase /
    	RewriteRule ^(media/.*)$ - [L]
    	RewriteCond %{REQUEST_URI} !(django.fcgi)
    	RewriteRule ^(.*)$ django.fcgi/$1 [L]

7. 搞定

	好了, 就酱紫了! 现在可以访问一下你新建的子域名了! 我建立的子域名是"lab", 所以访问的就是 [http://lab.v2nb.com](http://lab.v2nb.com) . 看到django的字样了吧?   

	这里只是配置完了Web服务的部分, Django部分还需要自己再配置一下, 或者直接放上你自己的Django网站:)   

	如果有需要, 可以再修改.htaccess, 或者参考我参考的帖子:) 

8. 参考

	[http://www.bluehostforum.com/showthread.php?t=715](http://www.bluehostforum.com/showthread.php?t=715)

	[http://wiki.dreamhost.com/index.php/Django#Setup](http://wiki.dreamhost.com/index.php/Django#Setup)

	[http://www.djangoproject.com/documentation/fastcgi/](http://www.djangoproject.com/documentation/fastcgi/)

	[http://blog.donews.com/limodou/archive/2006/03/29/799059.aspx](http://blog.donews.com/limodou/archive/2006/03/29/799059.aspx)

	[http://svn.saddi.com/py-lib/trunk/fcgi.py](http://svn.saddi.com/py-lib/trunk/fcgi.py)
