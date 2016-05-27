---
date: 2007-09-05 16:59:00
type: post
title_en: 2007-09-05-install-subversion-on-mtdv
title: 在MT(dv)上安装Subversion
wordpress_id: 395
tags:
- tech
- mt
- subversion
- svn
---

安装Subversion需要服务器上之前安装好yum, 没有安装请参考我的另一篇文章: [在MT(dv)安装yum](http://web.archive.org/web/20071012171712/http://nickcheng.com/2007/09/05/install-yum-on-mtdv/)

以下操作如无法进行请确认自己是以root身份登录(命令行下执行su指令,输入申请的root权限密码即可)!
  
* MT(dv) 默认安装有Subversion 1.1.4, 可以查看一下      

		svn --version
   
* 在自己的svn目录(/var/www/vhosts/your_domain/subdomains/your_subdomain/svn/)下建立SVN版本库目录      

		mkdir repo
   
* 在新建的目录建立SVN版本库      

		svnadmin create repo
   
* 然后更改目录的权限, 包括里面的子目录. 这一步很重要, 要不最后是无法访问的      

		chmod 777 repo -R

上面这些是准备工作, 接下来是配置Apache, 让我们的Subversion 启用Web Access
  
* 进入svn目录下的配置文件目录conf      

		cd /var/www/vhosts/your_domain/subdomains/your_subdomain/conf
   
* 建立vhost.conf文件. 用任意的编辑器均可. 本来打算使用emacs, 但MT默认没有安装, 只要使用vi      

		vi vhost.conf
   
* vhost.conf 文件内容如下      

		# svn.server.com -- vhost.conf file           
		<location />            
		DAV svn # 告诉Aapche加载svn模块来处理请求            
		SVNPath /var/www/vhosts/your_domain/subdomains/your_subdomain/repo # 指定SVN版本库路径            
		AuthType Basic # 身份验证方式            
		AuthName "Subversion Repository"            
		AuthUserFile /etc/svn-auth-file # 身份验证数据存放的路径文件            
		Require valid-user            
		</location>            
   
* 我们在配置文件定义了用户访问需要经过进行身份验证, 所以我们还要建立访问用户.      

		htpasswd -c /etc/svn-auth-file your-name
   
* 好了, 我们都完成了, 进行最后一步, 重启Apache      

		/usr/local/psa/admin/sbin/websrvmng -a -v

