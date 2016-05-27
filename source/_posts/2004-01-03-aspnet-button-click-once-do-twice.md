---
date: 2004-01-03 23:06:00
type: post
title_en: 2004-01-03-aspnet-button-click-once-do-twice
title: 关于asp.net中,点击按钮一次,响应两次的问题
wordpress_id: 65
tags:
- tech
---

前些日子做了一个简单小程序,出了点儿问题,后来解决了,在此总结一下...  
  
问题很简单.我用vs.net在一个aspx页面上放了一个  
程序代码:

`<asp:Button ID="Add" OnClick="AddClick" Runat="server" Text="Add" />`

然后,在后台的cs代码里写了这么一段  
程序代码:

	protected void AddClick(object sender, System.EventArgs e)  
	{  
	if(Session["BasketCount"]!=null)  
	{  
	int i=(int)Session["BasketCount"];  
	i++;  
	Session["BasketCount"]=(object)i;  
	}  
	else  
	{  
	Session["BasketCount"]=1;  
	}  
	}
  
我的本意是,在点击按钮以后,购物篮对应的这个Session变量就加1.可是当我执行的时候,我却发现,每一次我点击按钮,这个变量竟然增加2.我百思不得其解...  
  
后来,在CSDN中,我得到了帮助,解决了这个问题.  
  
问题的原因就在于vs.net自动生成的代码.大家看这行代码:  

程序代码:

`this.Add.Click += new System.EventHandler(this.AddClick);`

我在添加这个Button控件的时候,已经写上了OnClick事件对应的方法,但是在我双击这个控件添加cs代码的时候,vs.net又在 InitializeComponent()方法里添加了如上的代码,这样一来,每次点击按钮,就会将这两段代码分别执行,就导致了Session变量在每次点击后增加2的情况.  
  
vs.net是一个很强大的工具,但是我们要熟悉他,才能更好的让他为我们服务.像我这样对vs.net还不够熟悉,没有全面理解vs.net的工作方式,所以就导致了这个错误的发生.

[](http://www.icbean.com/nickcheng/default.asp?cat=2)
