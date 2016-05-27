---
date: 2007-02-07 09:18:04
type: post
title_en: the-problem-of-the-changed-name-of-attachment-when-sending-chinese-attachment-in-thunderbird
title: Thunderbird发送中文附件自动改名的问题
wordpress_id: 336
tags:
- life
---

一直没当成个事儿! 前段时间也碰到了这个情况, 只是把文件打了一个zip包重新发了一下, 也没有深究. 今天又有同事抱怨说我发的邮件的附件被改名, 于是Google之. 原来是因为Thunderbird太先进而导致没有考虑中文的一个bug.

具体原因大家可以参考[这个文章](http://hi.baidu.com/jarryleo/blog/item/ee91bdfd95d4ed1609244d99.html), 写的比较清楚了, 想更进一步了解的同学可以阅读[RFC2231](http://rfc.net/rfc2231.html)和[RFC2047](http://rfc.net/rfc2047.html)

解决方法也很简单. 在Thunderbird中, 工具->首选项->高级->配置编辑器. 然后找到"mail.strictly_mime.parm_folding", 把默认值2改为0就搞定了! 自己试试吧!
