---
date: 2010-02-20 21:10:58
type: post
title_en: memo-on-using-pymssql
title: 使用pymssql备忘
wordpress_id: 518
tags:
- tech
- db
- mssql
- pymssql
- python
- server
- sql
---

最近需要用Python来操作SQL Server, 所以找来了一些库试用.

简单搜索了一下, 看到pymssql是被提及最多的, 所以就决定用他了. 使用过程中有些小的地方需要注意, 特此备忘一下. 也能让别人少走点儿弯路(说不定我这个反而是弯路? whatever...)
	
* 我是在windows下使用的. 如果在import pymssql的时候出现DLL找不到的异常, 可以尝试把pymssql的egg解压缩为目录就好了.
* 调用存储过程的方式:
cur.execute('sp @param1=%s, @param2=%s',(param1, param2))
* 如果查询结果集中有ntext类型数据, pymssql不能正确处理. 可以在sql语句中进行类型转换.

其他功能类似的模块还有pyodbc, adodbapi, 不过我都没有试用.
