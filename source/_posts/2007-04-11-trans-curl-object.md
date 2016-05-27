---
date: 2007-04-11 20:23:05
type: post
title_en: 2007-04-11-trans-curl-object
title: "[翻译]Curl对象"
wordpress_id: 355
tags:
- tech
- curl
- translate
---

Curl对象

Curl对象有如下方法

close() 无返回值

> 对应于libcurl的curl_easy_cleanup方法. 在一个Curl对象不再有任何引用的时候, pycurl会自动调用这个方法. 这个方法也可以被显式调用.

perform() 无返回值

> 对应于libcurl的curl_easy_perform方法.

setopt(option, value) 无返回值

> 对应于libcurl的curl_easy_setopt方法.  option参数对应于libcurl的CURLOPT_*这一系列常量. 要注意的是, 在这个方法里要去掉CURLOPT_的前缀. value参数的取值类型取决于option参数, 它可以是字符串, 整型变量, 长整型变量, 文件对象, 列表对象或者方法.

例子

	import pycurl
	c = pycurl.Curl()
	c.setopt(pycurl.URL, "http://www.python.org/")
	c.setopt(pycurl.HTTPHEADER, ["Accept:"])
	import StringIO
	b = StringIO.StringIO()
	c.setopt(pycurl.WRITEFUNCTION, b.write)
	c.setopt(pycurl.FOLLOWLOCATION, 1)
	c.setopt(pycurl.MAXREDIRS, 5)
	c.perform()
	print b.getvalue()
	...

getinfo(option) 返回值:Result

> 对应于libcurl的curl_easy_getinfo方法. option参数对应于libcurl的CURLINFO_*常量, 使用的时候要去掉CURLINFO_前缀. 方法的返回值Result类型可能是整数, 浮点数或字符串, 这取决于option参数. getinfo方法应当在perform方法调用完毕后进行调用.

例子

	import pycurl
	c = pycurl.Curl()
	c.setopt(pycurl.URL, "http://sf.net")
	c.setopt(pycurl.FOLLOWLOCATION, 1)
	c.perform()
	print c.getinfo(pycurl.HTTP_CODE), c.getinfo(pycurl.EFFECTIVE_URL)
	...

--> 200 "http://sourceforge.net/"

errstr() 无返回值

> 以字符串形式返回当前示例的错误缓冲区内容
