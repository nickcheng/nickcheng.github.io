---
date: 2003-12-22 06:26:00
type: post
title_en: study-aspnet-application-state
title: 学习ASP.NET-初探Application状态
wordpress_id: 56
tags:
- tech
---

大家都知道在ASP.NET中，浏览器和Web服务器之间的连接是所谓的“无状态连接”。整个连接过程如下：  
  
1. 连接到服务器  
2. 告诉服务器访问者希望访问的内容  
3. 服务器返回访问者需要的内容  
4. 和服务器断开连接，同时丢失所有的用户信息  
  
正是这样，我们才会用到Application、Cookie、Session这些东西来达到保存特定的用户信息的目的，在本文中我们要谈的是Application。  
  
Application的原理是在服务器端建立一个状态变量，来存储所需的信息。要注意的是，首先，这个状态变量是建立在内存中的，其次是这个状态变量是可以被网站的所有页面访问的。这就意味着它只能存储一些要公布的信息，而不能存储一些比较个人的信息了！  
  
下面看一个例子：  
  
test1.aspx
	
	<%@ Page Language="C#"%>  
	<html>  
	<body>  
	<%Application["CompanyTelephone"]="123456789";%>  
	<b>Application state changed successfully</b>  
	</body>  
	</html>

test2.aspx
	
	<%@ Page Language="C#"%>  
	<html>  
	<body>  
	<b>Company Telephone =  
	<%  
	Response.Write(Application["CompanyTelephone"]);  
	%>  
	</b>  
	</body>  
	</html>

p.s. 以上是两个文件，要分开建立。  
  
在浏览器中调用test1.aspx文件，你会看到浏览器中显示：  
  
	Application state changed successfully  
  
这意味着我们成功地建立了一个Application状态。然后，再调用test2.aspx文件，这时就可以看到我们要的结果了：  
  
	Company Telephone = 123456789  
  
以上看到的是使用Application状态的一般情况。那大家有没有想过其它的情况？比如说当你成功的建立了Application状态以后（test1.aspx），服务器突然断电或者被重新启动了。  
  
这样问题就来了。如果真的发生了上述的情况，那么我们再运行test2.aspx后就不会看到我们要的结果了。所以为了避免上述的情况发生，我们应该在启动网站的时候，就配置应用程序状态。在此我们就要使用global.asax文件。  
  
//global.asax

	<script language="c#" runat="server">  
	void Application_OnStart()  
	{  
		Application["CompanyTelephone"]="123456789";  
	}  
	</script>

建立如上文件以后，将它放在Web应用程序的根文件夹中。这样一来，当Web应用程序启动的时候，ASP.NET会自己寻找global.asax文件。如果找到了，就再在其中寻找Application_OnStart()函数。如果这个函数存在，则运行其中的代码。  
  
好了，这样一来，即使我们没有运行test1.aspx，test2.aspx还是会得到我们所要的结果的！
