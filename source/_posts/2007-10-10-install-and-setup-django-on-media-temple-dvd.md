---
date: 2007-10-10 17:02:00
type: post
title_en: 2007-10-10-install-and-setup-django-on-media-temple-dvd
title: 在Media Temple(dv)上安装配置Django
wordpress_id: 398
tags:
- tech
- django
- dv
- install
- mediatemple
- mt
- setup
---

在Media Temple(dv)上安装使用Django

选择 MT , 除了他那些知名的客户群, 还看上了他 VPS 系统的高可配置性. 独立的虚机可以让你在上面安装任何你需要的东西, 当然, 你也要懂得怎么去操作.

自己的 Django 项目已经有些雏形了, 所以也要考虑让他能在 MT 上运行了. 虽然前段时间 MT 对他的 (gs) 服务提供了 Django 的支持, 但是 (dv) 服务还是没有官方的 Django 支持, 所以我只能自己动手来安装配置了!

经过一番摸索和尝试, 以及 Richard 同学(这位同学是我在 Django 的 maillist 上找到的可以骚扰的人^_^)的帮助, 我终于在自己的站点上看到了”Worked”的字样. 自己在网上搜索相关资料的时候一直没有看到有人写在 MT 上安装 Django 的经验, 那么我就作为第一个吃螃蟹的人吧, 希望大家在搜索”mt django”关键字的时候能搜到我的文章:) (是否需要再写一篇英文的?)

好吧, 我们开始干活了! 大家在模仿的时候请注意修改你自己的域名和子域名.
  
* 在自己的域名下建立一个子域名, 方便我们干活. 我在我的 nickcheng.com 域名下建立了一个 lab.nickcheng.com 子域名. 这个工作在 plesk 下就可以搞定. 
* 取得 MT 的 Shell 权限, 并且获得自己的 root 密码, 因为我们需要比较高的权限来做这些事情. root 密码需要在 MT 中提交一个 Support 来获取. 
* 进入 Shell 模式, 切换到 root 权限(使用 su 命令) 
* 切换到子域名 lab 所在的目录, 并建立 Django 目录, 下载/解压缩 Django

		cd /var/www/vhosts/nickcheng.com/subdomains/lab          
		mkdir django          
		cd django          
		wget http://www.djangoproject.com/download/0.96/tarball/          
		tar xzvf Django-0.96.tar.gz          

* 安装 Django       

		cd /var/www/vhosts/nickcheng.com/subdomains/lab/Django-0.96          
		python setup.py install          

上面的步骤如果没错的话, Django 就已经在你的服务器上安装好了. 为了验证一下, 我们可以使用如下的步骤.     

	python        
	import django        

如果没有报错, 那么就证明我们的已经成功安装了 Django. 接下来是配置 Django 站点了.
  
* 首先不建议把你的 Django 网站的源代码放在 httpdocs 目录下, 因为这样如果操作不当, 会有可能给别人下载你源码的机会, 所以我还是把 Django 网站的源代码放在了之前建立的 django 目录中.       

		cd /var/www/vhosts/nickcheng.com/subdomains/lab/django          
		django-admin.py startproject djangotest          

* 建立了 djangotest 这个 django 网站后, 就是最重要的配置步骤了. 我们先切换到配置文件所在的目录       

		cd /var/www/vhosts/nickcheng.com/subdomains/lab/conf          
   
* 这时这个目录应该是空的, 我们需要自己建立配置文件. 因为 MT 自带了 vi, 所以我用它来做这个事情       

		vi vhost.conf          
   
* 关于 vi 的操作还请大家自己学习. 我贴一下我的 vhost.conf 文件的内容       

        <location>          
            SetHandler python-program          
            PythonPath "['/var/www/vhosts/nickcheng.com/subdomains/lab/django/'] + sys.path"          
            PythonHandler django.core.handlers.modpython          
            SetEnv DJANGO_SETTINGS_MODULE djangotest.settings          
            PythonDebug On          
        </location>

	* 第一行, Location 后的路径不是指磁盘上的路径, 而是用户访问网站的路径. 我这里用 “/” 是指用户访问http://lab.nickcheng.com时的配置. 
	* 第二行, 指明这个路径下使用的Handler, 这里使用python 
	* 第三行, 指明你的 Django 网站源码所在的路径. 需要注意的是, 这里的路径要写你执行 django-admin.py 文件时所在的目录. 
	* 第五行, 要写完整你建立的 project 的 settings.
   
* 配置完成后, 我们需要重启服务来让他生效.       

		/usr/local/psa/admin/sbin/websrvmng -a -v

现在访问 http://lab.nickcheng.com, 应该可以看到 “It worked!” 的字样了:) 我们成功了
