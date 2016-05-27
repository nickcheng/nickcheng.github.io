---
date: 2007-10-12 17:03:00
type: post
title_en: pay-attention-to-the-python-egg-when-use-modpython-and-django
title: mod_python和django使用需要注意python egg
wordpress_id: 399
tags:
- tech
- django
- egg
- modpython
- python
---

不认识上面几个英文的朋友请忽略本文, 谢谢:)

昨天在配置Django的数据库的时候, 发现了一个奇怪的问题.

在我将数据库设置配置完成后, 在本地用manage.py runserver执行访问都没有问题, 但是放到服务器上用apache+mod_python的方式执行访问的时候, 就会报错. 而且更诡异的是每次报错都不一样. 我观察了一下, 发现基本就是两种错误在来回的报! 一个是说我的middleware有问题, 另一个说是在使用一些egg文件时有问题.

连忙上网搜了一圈, 找到了一些类型的情形, 大家的基本解决方案都指向了django网站的一个网页(看来还是官网好啊).

[using eggs with mod_python](http://web.archive.org/web/20071014010413/http://www.djangoproject.com/documentation/modpython/#using-eggs-with-mod-python)

看完这个介绍以后, 终于明白了问题的所在,剩下的就是按步骤来做了! 不过这里还有一个小技巧.

报egg使用有问题的错误时, 错误信息中写的很详细, 大概意思是说因为我没有配置[using eggs with mod_python](http://web.archive.org/web/20071014010413/http://www.djangoproject.com/documentation/modpython/#using-eggs-with-mod-python) 中所说的cache目录, 所以默认要使用”/.python-eggs”目录作为cache目录. 而我的服务器上并没有这个目录, 所以才会报错.

这样就简单了, 我就建一个这个目录呗, 再把权限一改, 再一试, 嘿嘿...齐活!

不想麻烦的朋友, 如果遇到这个问题能看到他需要的目录, 可以采用我的方法:)
