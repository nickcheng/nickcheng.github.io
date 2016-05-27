---
date: 2006-11-17 17:36:15
type: post
title_en: 2006-11-17-solved-char-problem-of-subversion
title: Subversion 乱码问题解决
wordpress_id: 308
tags:
- tech
---

13日Subversion 1.4.2发布了, 今天下一个到新电脑上, 准备大规模使用.

不过当安装好以后, 在命令行下试用"svn"指令时, 发现提示信息全变成了乱码! 郁闷啊, 于是上网搜了一下, 好在已经有人遇到了同样的问题, 所以我的问题也迎刃而解了! 为了让更多的有这个问题的人不再郁闷, 我也写写, 方便别人搜索:)

首先, 我用的Windows的操作系统!

这其实是一个地区编码匹配的问题, 解决方法也是很简单! 就是在系统的环境变量中增加两个就ok了, 分别是:

	LANG=zh_CN.UTF8
	APR_ICONV_PATH=SVN目录\iconv(我的是D:\Tools\svn\iconv)

ok, 就这样简单:)

原始地址在这里:

<http://svn.haxx.se/users/archive-2005-03/0461.shtml>
