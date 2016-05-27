---
date: 2007-09-05 16:58:00
type: post
title_en: 2007-09-05-install-yum-on-mtdv
title: 在MT(dv)安装yum
wordpress_id: 394
tags:
- tech
- install
- mt
- subversion
- svn
- yum
---

前面说了自己已经成功的在自己的MT(dv)服务器上部署了Subversion服务, 而且启用了在 Apache 下的 Web Access, 所以这里单独写文章记录一下, 一来给自己做一个备忘, 二来可以帮助有类似需求的朋友:)

在MT(dv)上安装Subversion需要用到yum, 所以这篇文章单独来讲如何安装yum

步骤如下
  
* 建立一个子域名. 如: svn.domain.com 
* 开通自己域名的SSH功能 
* 向MediaTemple申请root权限

上面是准备工作, 下面是正式的操作步骤
  
* 通过SSH, 登录自己的服务器 
* 使用su指令切换为root身份 
* 切换目录到你建立的子域名所在的目录. 如:/var/www/vhosts/domain_name/subdomains/svn 
* 下载yum在centos上的安装包      

		wget http://centos.mirror.vpslink.com/centos-4/4.5/os/i386/CentOS/RPMS/yum-2.4.3-3.el4.centos.noarch.rpm
   
* yum安装包会有一些依赖文件, 也下载一下      

		rpm -ivh --nodeps http://centos.mirror.vpslink.com/centos-4/4.5/os/i386/CentOS/RPMS/libxml2-python-2.6.16-10.i386.rpm           
		rpm -ivh --nodeps http://centos.mirror.vpslink.com/centos-4/4.5/os/i386/CentOS/RPMS/python-elementtree-1.2.6-5.el4.centos.i386.rpm            
		rpm -ivh --nodeps http://centos.mirror.vpslink.com/centos-4/4.5/os/i386/CentOS/RPMS/python-sqlite-1.1.7-1.2.1.i386.rpm            
		rpm -ivh --nodeps http://centos.mirror.vpslink.com/centos-4/4.5/os/i386/CentOS/RPMS/rpm-python-4.3.3-22_nonptl.i386.rpm            
		rpm -ivh --nodeps http://centos.mirror.vpslink.com/centos-4/4.5/os/i386/CentOS/RPMS/python-urlgrabber-2.9.8-2.noarch.rpm
  
* 安装yum      

		rpm -Uvh yum-2.4.3-3.el4.centos.noarch.rpm
   
* 检查一下是否安装好了      

		rpm -q yum

好了, yum可以使用了:)
