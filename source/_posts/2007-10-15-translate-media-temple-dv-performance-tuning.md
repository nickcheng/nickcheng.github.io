---
date: 2007-10-15 17:05:00
type: post
title_en: 2007-10-15-translate-media-temple-dv-performance-tuning
title: "[翻译]Media Temple (dv) 服务器性能优化"
wordpress_id: 400
tags:
- tech
- dv
- media
- mt
- temple
- translate
- tuning
---

原文见: [http://kb.mediatemple.net/article.php?id=771](http://web.archive.org/web/20071111042750/http://kb.mediatemple.net/article.php?id=771)

概述

本文总结了优化 (dv) 服务器的方法. 包括运行程序时使用尽可能少的内存和资源, 逐渐提升的系统稳定性, 以及在高负载条件下的高可用性.

征兆
  
* 频繁的 Apache(httpd) 当机 
* 缓慢的服务器响应速度 
* “服务器无法访问”(Server unreachable)的错误信息 
* QoS 警报中的 kmemsize 警告(在Virtuozzo的Plesk控制面板中) 
* QoS 警报中的 privvmpages 警告(在Virtuozzo的Plesk控制面板中)

需要的一些准备
  
* 你(dv)服务器的[SSH权限](http://web.archive.org/web/20071111042750/http://kb.mediatemple.net/article.php?id=110)和[Root访问权](http://web.archive.org/web/20071111042750/http://kb.mediatemple.net/article.php?id=625)限 
* 一些最基础的[vim编辑器](http://web.archive.org/web/20071111042750/http://www.vim.org/)的知识

详细描述

注意: 下面的几篇文章的难度是逐步提高的, 性能调优的力度也是逐渐增大. 所以我们建议你按照顺序来使用这些文章. 在使用每篇文章前, 最好先在前一篇的基础上进行服务器稳定性和功能性的测试!

第一部分: [Apache 性能调优基础(httpd)(英文)](http://web.archive.org/web/20071111042750/http://kb.mediatemple.net/article.php?id=246)

这篇文章指导你把 Apache 的 httpd.conf 文件中的 Timeout 和 MaxClients 参数调低. 这些参数可以降低 Apache 服务器的内存消耗并提高可用性.
  
* 完成本文的操作大概需要的时间: 5-20 分钟 
* 难度级别(1-5, 5最难): 2 
* 可能的内存占用减少: 20兆-60兆

第二部分: [MySQL 性能调优基础(mysqld)(英文)](http://web.archive.org/web/20071111042750/http://kb.mediatemple.net/article.php?id=258)

这篇文章知道你修改 MySQL 的 my.cnf 配置文件来启用查询缓存. 虽然这样会增加 MySQL 的内存消耗, 但是性能却有很大程度的提高.
  
* 完成本文的操作大概需要的时间: 5-15 分钟 
* 难度级别(1-5, 5最难): 2 
* 内存消耗增加: 16兆-32兆

第三部分: [其他性能调优(英文)](http://web.archive.org/web/20071111042750/http://kb.mediatemple.net/article.php?id=770)

这篇文章指导你限制或关掉一些你服务器上不需要的服务. 也许你只需要本文的一部分内容, 所以有些操作可能和例子不太一样.
  
* 完成本文的操作大概需要的时间: 5-15 分钟 
* 难度级别(1-5, 5最难): 3 
* 可能的内存占用减少: 60兆-130兆
