---
date: 2003-12-11 11:41:00
type: post
title_en: connect-to-access-and-sqlserver-use-csharp
title: 用ASP.NET/C#连接Access和SQL Server数据库
wordpress_id: 47
tags:
- tech
---

连接Access

首先看一个例子代码片断:

程序代码:

	using System.Data;
	using System.Data.OleDb; `
	
	string strConnection="Provider=Microsoft.Jet.OleDb.4.0;";
	strConnection+=@"Data Source=C:\BegASPNET\Northwind.mdb";OleDbConnection objConnection=new OleDbConnection(strConnection);
	
	objConnection.Open();
	objConnection.Close();

--------------------------------------------------------------------------------

解释:

连接Access数据库需要导入额外的命名空间,所以有了最前面的两条using命令,这是必不可少的!

strConnection这个变量里存放的是连接数据库所需要的连接字符串,他指定了要使用的数据提供者和要使用的数据源.

"Provider=Microsoft.Jet.OleDb.4.0;"是指数据提供者,这里使用的是Microsoft Jet引擎,也就是Access中的数据引擎,asp.net就是靠这个和Access的数据库连接的.

"Data Source=C:\BegASPNET\Northwind.mdb"是指明数据源的位置,他的标准形式是"Data Source=MyDrive:MyPath\MyFile.MDB".

ps:

1. "+="后面的"@"符号是防止将后面字符串中的"\"解析为转义字符.
2. 如果要连接的数据库文件和当前文件在同一个目录下,还可以使用如下的方法连接:

		strConnection+="Data Source=";
		strConnection+=MapPath("Northwind.mdb");

	这样就可以省得你写一大堆东西了!

3. 要注意连接字符串中的参数之间要用分号来分隔.

"OleDbConnection objConnection=new OleDbConnection(strConnection);"这一句是利用定义好的连接字符串来建立了一个链接对象,以后对数据库的操作我们都要和这个对象打交道.

"objConnection.Open();"这用来打开连接.至此,与Access数据库的连接完成.其余操作(插入,删除...)请参阅相关书籍

连接SQL Server

例子代码片断:

程序代码:

	using System.Data;
	using System.Data.SqlClient;...
	
	string strConnection="user id=sa;password=;";
	strConnection+="initial catalog=Northwind;Server=YourSQLServer;";
	strConnection+="Connect Timeout=30";
	
	SqlConnection objConnection=new SqlConnection(strConnection);
	
	...
	
	objConnection.Open();
	objConnection.Close();
	
	...

解释:

连接SQL Server数据库的机制与连接Access的机制没有什么太大的区别,只是改变了Connection对象和连接字符串中的不同参数.

首先,连接SQL Server使用的命名空间不是"System.Data.OleDb",而是"System.Data.SqlClient".

其次就是他的连接字符串了,我们一个一个参数来介绍(注意:参数间用分号分隔):

"user id=sa":连接数据库的验证用户名为sa.他还有一个别名"uid",所以这句我们还可以写成"uid=sa".

"password=":连接数据库的验证密码为空.他的别名为"pwd",所以我们可以写为"pwd=".

这里注意,你的SQL Server必须已经设置了需要用户名和密码来登录,否则不能用这样的方式来登录.如果你的SQL Server设置为Windows登录,那么在这里就不需要使用"user id"和"password"这样的方式来登录,而需要使用"Trusted_Connection=SSPI"来进行登录.

"initial catalog=Northwind":使用的数据源为"Northwind"这个数据库.他的别名为"Database",本句可以写成"Database=Northwind".

"Server =YourSQLServer":使用名为"YourSQLServer"的服务器.他的别名为"Data Source","Address","Addr".如果使用的是本地数据库且定义了实例名,则可以写为"Server=(local)\实例名";如果是远程服务器,则将"(local)"替换为远程服务器的名称或IP地址.

"Connect Timeout=30":连接超时时间为30秒.

在这里,建立连接对象用的构造函数为:SqlConnection.

其余的就和Access没有什么区别了!
