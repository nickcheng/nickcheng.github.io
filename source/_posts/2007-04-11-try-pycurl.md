---
date: 2007-04-11 00:18:29
type: post
title_en: 2007-04-11-try-pycurl
title: 初试Pycurl
wordpress_id: 354
tags:
- tech
- curl
- pycurl
- python
---

今天调试爬虫的时候在网上找文章, 恰巧找到了Pycurl的介绍文章, 大概看了一下并浏览了[项目主页](http://pycurl.sourceforge.net/), 发现这个东西真的挺好的, 也挺适合我的. 我应该考虑在爬虫里使用这个东东:)

> supporting FTP, FTPS, HTTP, HTTPS, GOPHER, TELNET, DICT, FILE and LDAP. libcurl supports HTTPS certificates, HTTP POST, HTTP PUT, FTP uploading, kerberos, HTTP form based upload, proxies, cookies, user+password authentication, file transfer resume, http proxy tunneling and more!

再看看人家的功能, 真是一个让人偷懒的东西啊! 这下子连代理服务器的功能都省了. 而且这个东东是用C写的, 效率自然也更高, 使用它? 何乐而不为呢?

顺手从项目主页拉下来一个[win32的版本](http://pycurl.sourceforge.net/download/pycurl-ssl-7.15.5.1.win32-py2.4.exe) [[2]](http://pycurl.sourceforge.net/download/pycurl-ssl-7.15.5.1.win32-py2.5.exe). 试了几个[示例代码](http://pycurl.cvs.sourceforge.net/pycurl/pycurl/tests/) [[2]](http://pycurl.cvs.sourceforge.net/pycurl/pycurl/examples/), 还不错! 不过要想用好这个东西还是有一点门槛的! 因为Pycurl本身是[libcurl](http://curl.haxx.se/libcurl/)的一个封装, 所以在使用pycurl的时候还是需要参考[libcurl的文档](http://curl.haxx.se/libcurl/c/)的, 而那个文档又是针对c的, 这里就有那么一点曲线啦!

对于Pycurl的Curl对象, 那个setopt方法是个重头戏, 需要好好研究[参考文档](http://curl.haxx.se/libcurl/c/curl_easy_setopt.html)才能玩得转!
