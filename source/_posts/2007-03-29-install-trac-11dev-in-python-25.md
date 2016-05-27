---
date: 2007-03-29 23:25:44
type: post
title_en: 2007-03-29-install-trac-11dev-in-python-25
title: 在Python2.5下安装Trac 0.11dev
wordpress_id: 352
tags:
- tech
- installation
- python
- trac
---

搞定了Apache和Subversion以后, 准备搞定Trac.

照例是到网上搜了一大圈, 找了一堆的参考资料. 不过一篇一篇的看过以后发现所有的文章都是在讲基于Python 2.4的Trac安装, 我心里一悬, 也不知道这Python 2.5上安装会不会有问题! 先不管三七二十一, 比葫芦画瓢先!

于是开始准备一些必须的软件, 果不其然, 这一步就遇到了问题! 我找不到对应Python 2.5的ClearSilver. TNND, 真是出师未捷身先死啊! 不甘心......

继续在Trac官方网站翻阅资料......哈哈...功夫不负有心人, 被我找到了一篇[Trac with Python 2.5](http://trac.edgewall.org/wiki/TracOnWindows/Python2.5). 这应该是Python 2.5下的东东了吧! 用劲看完了这份文档, 发现这讲的是更新潮的事情--安装正在开发的Trac 0.11dev版本.

想了一下, 自己也不是用Trac管理太重要的东西, 而且实在不行还可以一直跟着svn的trunk升级嘛! 于是乎, 下定了决心跟着dev版本走!

这0.11dev版本的一大好处是不再使用ClearSilver, 而是使用Genshi来取而代之, 这Genshi是有Python 2.5版本滴!!赞!

看到这里可别以为以后的道路都是平坦的. 这过程和人生是一样的, 一个坎坷接着一个坎坷......

按照官方文档, 我下载了对应版本的Genshi和Trac. 在安装Trac的时候又出问题了. 我最新Checkout出来的Trac说我下载的Genshi的版本低......ft...这还官方文档呢...~~

不怕, 咱再自己去Checkout最新的Genshi. 你要是以为这就好了的话, 那你就又错了! 这回Trac改口说我的Genshi版本太高了......我再次摔倒了...

那怎么办? 还好安装Trac的时候给的提示信息比较全. 看到Trac提示的信息说需要的Genshi版本不能高于Genshi 0.4dev-r510. 那好我就去Checkout 509版本的Genshi......这次终于好了...前面几个坎差点儿把我摔背过气去......

后面的康庄大道就好走多了. 安装了svn-python的绑定后就可以自己用trac-admin来建个工程, 再用tracd发布玩玩了.

最后配置一下apache, 用apache统一发布, 哈哈, 起活!

=======

安装步骤

* 下载必须软件
	* Genshi 0.4 r509: `svn co http://svn.edgewall.org/repos/genshi/trunk@509`
	* Trac 0.11dev: `svn co http://svn.edgewall.org/repos/trac/trunk`
	* SVN的Python绑定: `http://subversion.tigris.org/downloads/svn-python-1.4.3.win32-py2.5.exe`
* 安装
	* 安装Genshi
	* 安装SVN的Python绑定
	* 安装Trac
* 配置Apache
	* 在conf中增加如下代码
	
			<Location "/trac">
			    SetHandler mod_python
			    PythonHandler trac.web.modpython_frontend
			    PythonOption TracEnvParentDir "d:/trac"
			    PythonOption TracUriRoot /trac
			</Location>
