---
date: 2007-03-29 21:22:39
type: post
title_en: 2007-03-29-install-and-config-subversion-143-in-apache-224
title: 在Apache2.2.4下安装配置Subversion1.4.3
wordpress_id: 351
tags:
- tech
- apache
- installation
- subversion
- svn
---

中午吃完饭, 回来配置自己的Droupnir. 对于Droupnir, 计划在上面安装支持Subversion的Trac. 作为自己的项目管理平台和配置管理平台.

一篇先写安装配置Subversion

去Subversion的网站下载最新的Subversion, 我下载的是这个版本:

[http://subversion.tigris.org/files/documents/15/36797/svn-1.4.3-setup.exe](http://subversion.tigris.org/files/documents/15/36797/svn-1.4.3-setup.exe)

[](http://subversion.tigris.org/files/documents/15/36797/svn-1.4.3-setup.exe)因为Droupnir上已经安装好了Apache 2.2.4, 所以我就直接安装Subversion. 我以为一切都会很顺利, 可是...我错了...安装过程中出现了一个错误, 然后Apache就不能启动了! 查了半天Google, 终于知道了原因--最新的Subversion 1.4.3 不支持Apache 2.2.4. 除非自己去Build Apache所需的module.

是又在网上找到了[别人build好的module](http://www.apachelounge.com/forum/viewtopic.php?p=6610), 虽然有[一些已知的问题](http://www.apachelounge.com/forum/viewtopic.php?p=6610), 但是应该还好! 这里需要注意, 这个编译好的module是用VC2005sp1编译的, 所以要求使用的Apache也是用VC2005sp1编译, [VC2005sp1编译的Apache在这里](http://www.apachelounge.com/download/binaries/httpd-2.2.4-win32-x86-ssl.zip), 使用这个版本的Apache还需要[Visual C++ 2005 Redistributable Package](http://www.apachelounge.com/download/vcredist_x86-sp1.exe). 安装的时候别忘了看readme哦!

装Subversion后, 他会自动修改Apache的conf. 不过你要是使用上面说的自己编译的Apache的话, 那就要自己去看看是不是在conf中加入了该加入的内容.

后就是把自己的SVN版本库用Apache发布了, 这一步就是配置Apache的conf了, 没有什么特别的, [SVNBook里写的很清楚](http://svnbook.subversion.org.cn/1.2/svn.serverconfig.httpd.html).

果需要权限配置的话, 可以参考[这篇帖子](http://www.iusesvn.com/bbs/thread-158-1-1.html), 里面写的很详细!

下面附上我整理的步骤

安装步骤

* 下载
	* http://www.apachelounge.com/download/binaries/httpd-2.2.4-win32-x86-ssl.zip
	* http://www.apachelounge.com/download/vcredist_x86-sp1.exe
	* http://subversion.tigris.org/files/documents/15/36797/svn-1.4.3-setup.exe
	* http://www.tomdonovan.net/download/mod_svn_143_apache_224.zip
* 安装Apache
	* 安装Visual C++ 2005 Redistributable Package
		* vcredist_x86-sp1.exe
	* 安装Apache
		* httpd-2.2.4-win32-x86-ssl.zip
* 安装Subversion
	* 安装官方SVN
		* svn-1.4.3-setup.exe
	* 安装为Apache 2.2.4编译的Subversion module
	* 用mod_svn_143_apache_224.zip中module目录里的文件替换Subversion/bin目录中的
	* 修改Apache的conf. 路径要正确
	
			LoadModule dav_module modules/mod_dav.so
			LoadModule dav_svn_module modules/mod_dav_svn.so
			LoadModule authz_svn_module modules/mod_authz_svn.so
		
	* 配置Apache的conf, 来映射svn repository
		* 在上一项配置后面写如下配置语法
		
				<Location /repos>
				DAV svn
				SVNPath /absolute/path/to/repository
				</Location>
			
		* 如果想支持多个有相同父目录的Subversion版本库, 则使用如下配置语法
		
				<Location /svn>
				DAV svn
				SVNParentPath /usr/local/svn
				</Location>
				
	* 配置Apache对Subversion版本库目录的访问权限
	* 建立密码文件
		* 在Apache的bin目录中运行"htpasswd -c passwd <username>"(<username>换成你自己的用户名), 按照提示输入两次密码, 会在当前目录下建立passwd文件, 将这个文件复制到根目录
	* 修改Apache的conf
	
			<Location /svn>
			DAV svn
			SVNListParentPath on
			SVNParentPath d:/svn
			AuthType Basic
			AuthName "Subversion repositories"
			AuthUserFile d:/passwd
			Require valid-user
			</Location>
