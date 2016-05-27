---
date: 2006-02-24 23:16:01
type: post
title_en: 2006-02-24-hit-by-django
title: 被Django折腾
wordpress_id: 218
tags:
- tech
---

这几天学习使用Python下的一个名叫Django的Web Framework的使用, 竟然看着[教程](http://www.woodpecker.org.cn/obp/django/django-stepbystep/newtest/doc/)也郁闷了两次, 讲讲经过吧!

1. **版本**

教程上写, 目前release出来的django的版本是0.91, 而教程是基于django的一个branch的, 名字叫做magic-removal, 貌似这个分支会成为0.92版本. 性急的我就看到了前半句, ok, 我想既然没有release出来, 那我就自己去SVN上自己拿去, 而且我竟然想当然的拿了trunk的版本, 然后就照着教程做了起来.

这可好, 教程第一节的例子就不能work, 一直报数据库模块找不到. 可教程上明明写这个版本的django是不用配置数据库就可以work的啊. 没办法, 只能求救于maillist list了.

第二天, 去review maillist list. 呵呵, 有人立刻指出我的问题. (我在问题里说了我拿的是trunk版本) 多谢多谢, 我这就去拿magic-removal分支! 拿下来一试, 嘿嘿, 还真好用! 此乃第一闷

2. **端口**

做到第六节, 一切按教程办妥, 就开始向往常一样启动服务器来测试一下.

	manage.py runserver

......
服务启动了, 不过竟然给我报了一个错误. 10030 XXXXXX

本来想着, 报错就报错吧, 能work就行! 嘿, 还真跟我较劲, 死活访问不了...没办法, 只能想辙解决了!

先到maillist 上搜了一通, 似乎没有人有这个问题, 然后又用google在官方网上搜了一通, 还是没有找到类似东东...这可如何是好呢? 百无聊赖, 只好看manage.py的帮助(直接执行这个就看到帮助了)

突然看到runserver命令后面可以跟一个参数来指定启动服务的端口! 我就灵机一动, 换个端口玩玩...

哈哈, 歪打正着! 我把默认的8000端口改成8080, 启动就成功了, 也没有报错! 不错,不错! 原来是这个该死的端口的问题...那为什么8000端口不能用呢? 我用netstat一看, 原来有另一个程序已经用了8000端口了, 所以我再启动服务的时候就不能用了!

拨开云出见月明了!!!(也不知道这一句对不对, 在google搜这句的时候竟然把google搜死了, 估计搜索结果有问题, 被GFW了=_=')
