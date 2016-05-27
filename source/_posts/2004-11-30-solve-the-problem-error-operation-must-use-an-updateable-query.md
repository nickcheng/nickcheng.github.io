---
date: 2004-11-30 23:59:00
type: post
title_en: 2004-11-30-solve-the-problem-error-operation-must-use-an-updateable-query
title: 错误“操作必须使用一个可更新的查询”原因及解决办法
wordpress_id: 99
tags:
- tech
---

翻译得比较匆忙，呵呵。  

错误信息：  

>Microsoft OLE DB Provider for ODBC Drivers error '80004005'  
[Microsoft][ODBC Microsoft Access 97 Driver] Operation must use an updateable query.  

或者是：  

>Microsoft JET Database Engine (0x80004005)  
操作必须使用一个可更新的查询。  
  
原因：  

有几个主要的错误原因：  

这个错误发生在当你的程序试图执行更新数据库或其它类似操作时。这是因为ADO由于以下的几个原因而不能够写数据库造成的。  

1. 最普遍的原因是匿名用户帐号(IUSR_MACHINE)对该数据库文件没有写权限。  

	要解决这个问题，在管理器中调整数据库文件的属性，让匿名用户有正确的权限。  

	当使用ACCESS数据库时，不仅要给文件写的权限，还要给该目录写 的权限，因为Jet需要在该目录建立一个.ldb文件。  

2. 第二个原因是数据库没有使用正确的模式打开。应该使用下面的方法打开。  

		SQL = "UPDATE Products Set UnitPrice = 2;"  
		Set Conn = Server.CreateObject("ADODB.Connection")  
		Conn.Mode = 3 '3 = adModeReadWrite  
		Conn.Open "myDSN"  
		Conn.Execute(SQL)  
		Conn.Close  

	注意默认的Mode是设置0(adModeUnknown),它是允许更新的。  

3. 还有可能是在ODBC管理器中将该DSN的只读选项选中。  
4. 你是在同时更新两个表中的字段，也会出现这个错误信息，解决办法是分开来更新  
这两个表中各自字段。  
5. 当你使用了一个从低版本中（如ACCESS2.0,ACCESS7.0）载入到高版本(ACCESS 2000) 中的查询时，在执行这个查询是会出现该错误。
