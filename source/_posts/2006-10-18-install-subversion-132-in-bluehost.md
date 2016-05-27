---
date: 2006-10-18 13:19:24
type: post
title_en: 2006-10-18-install-subversion-132-in-bluehost
title: 在BlueHost上安装Subversion 1.3.2
wordpress_id: 299
tags:
- tech
---

![Subversion](http://aragost.com/static/subversion.png)

稍微费了点儿劲, 在自己得BlueHost空间里装上了Subversion.

首先需要开通自己帐号得"SSH/Shell  Access", 原来可以直接在CPanel里自己直接选择开通, 可是现在不知道由于什么原因, 想要开通这个权限需要将自己得身份证复印件给他们传真或mail过去, 数码照片也可以(我就是传得照片), 难道他们也需要备案?

好在BlueHost得客服响应速度比较快, 这个过程大概半天就搞定了! 接下来就进入正题了!

从CPanel进入自己得Shell(还是选择那个"SSH/Shell  Access"). 连接上自己得服务器, IP就是你虚拟主机得IP, 用户名和密码也是和FTP那个一样, 端口号不用修改, 然后连接!

剩下得步骤我都是参考"[Installing Mephisto And Subversion in a Shared Hosting Enviroment](http://blog.matharvard.com/2006/9/21/mephisto-subversion)". 简单描述一下吧!

1. 建立一个"src"目录, 我们所有得操作都在这个目录里进行.  

		mkdir src

2. 进入目录  

		cd src

3. 下载subversion 1.3.2, 并解压缩  

		wget http://subversion.tigris.org/downloads/subversion-1.3.2.tar.gz  
		tar -xzvf subversion-1.3.2.tar.gz

4. 进入解压缩出来得目录  

		cd subversion-1.3.2

5. 配置, 编译, 安装  

		./configure --prefix=$HOME --without-berkeley-db --with-zlib --with-ssl  
		make  
		make install

好了, 这就全搞定了! 可以直接运行"svn --help"看看了

ps. 本来想安装最新得Subversion 1.4.0, 不过用上面方法在配置那一步过不去, 也没仔细研究, 所以就还是用1.3.2了.
