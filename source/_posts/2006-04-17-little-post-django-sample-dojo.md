---
date: 2006-04-17 22:59:52
type: post
title_en: 2006-04-17-little-post-django-sample-dojo
title: "记一小笔: django sample + dojo"
wordpress_id: 255
tags:
- tech
---

突发灵感, 在SVN上更新一下Django的MagicRemovel分支, 嘿嘿, 还真是更新了不少文件.

被我注意到的是多了一个Sample. 打开一看, 不出所料, Hello world! 这是惯例:) 不过用了很多种方法来say hello to the world. 从最简单的到有GET和POST数据的, 齐了:)

晚上在试验Dojo的时候, 发现了一个问题.

如果我在中加上onload方法, dojo的widget就会失效! 估计是dojo的实现也是通过body.onload来实现的, 如果我加上我自己的代码的话, 就把它的给冲掉了! 那怎么办呢? dojo的文档不是太全, 我search了一下邮件列表的achives, 找到了解决方法.

那就是使用dojo.addOnLoad()方法来加上自己的onload方法.

比如你原来要这么写

![code](http://nickcheng.zoto.com/img/original/b92270e5721043b922b2f2100649cf3d-.jpg)

那么现在就需要在head里这么写

![code](http://nickcheng.zoto.com/img/original/f5b9a9c120de36d429276d0d0a5e6ba4-.jpg)

这样就ok啦!
