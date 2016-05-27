---
date: 2004-11-19 21:23:00
type: post
title_en: 2004-11-19-how-zindex-working
title: HTML元素的Z-index属性是如何工作的
wordpress_id: 94
tags:
- tech
---

摘要
  
在一个Web页面上有很多种方法去把元素分类. 基于本文的目的和z-index属性, 我们可以把他们分为两类: 窗口类和非窗口类.  
  
窗口类元素  

	• <OBJECT> 标志元素  
	• ActiveX 控件  
	• Plug-ins  
	• 动态 HTML (DHTML) Scriptlets  
	• SELECT 元素  
	• Internet Explorer 5.01 以及早期版本中的IFRAMEs
 

**注意** 

ActiveX 控件是按照窗口类来实现的, 但实际上还有一部分是非窗口类的. 默认的, Microsoft Visual Basic 和Microsoft Foundation Class (MFC) 控件是窗口类的, 但是Active Template Library (ATL) 空间是非窗口类的.  
  
非窗口类元素  

	• 非窗口的ActiveX控件  
	• Internet Explorer 5.5和以后版本的IFRAMEs  
	• 大多数DHTML元素, 比如hyperlinks和 tables  
  
更多信息  

所有的窗口类元素在呈现时都会覆盖在非窗口类元素上面, 而不管他们的容器是什么样的. 然而在窗口类元素之间也是象非窗口类元素一样都是按照z-index属性来排列的.  
  
所有的非窗口类元素都是呈现在相同的MSHTML平面上, 而窗口类元素是呈现在单独的MSHTML平面上. 你可以利用z-index在同一个平面内随意操作元素, 但是不要把不通平面的元素混为一谈. 你可以分别重新排列不同平面上元素的z-index, 但是窗口类的平面是总在非窗口类平面之上的.  
  
在Internet Explorer 5中Z-index是怎么工作的  

Internet Explorer 5中, IFRAMEs是窗口类控件, 并且他按照z-index属性的顺序和其他窗口类控件排列在一起, 比如SELECT元素. 如果IFRAME的z-index值比SELECT元素的大, 那么IFRAME将会呈现在SELECT元素之上, 反之亦然. 如果z-index值相同, 那就要看元素在页面上的位置; 也就是说, 最后放上去的元素将会在前面的元素之上.  
  
下面的代码说明这一点:

	<HTML>  
	<HEAD>  
	<TITLE>Z-Index</TITLE>  
	<script>  
	function setindex()  
	{  
	div1.style.zIndex=text1.value;  
	select1.style.zIndex=text2.value;  
	getindexes();  
	}  
	
	function getindexes(){  
	text1.value=div1.style.zIndex;  
	text2.value=select1.style.zIndex;  
	text3.value=5;  
	}  
	</script>  
	</HEAD>  
	<BODY onload="getindexes()">  
	
	Div  
	<input type="text" value="" id=text1 name=text1 ><p>  
	
	Select  
	<input type="text" value="" id=text2 name=text2><p>  
	
	IFrame  
	<input type="text" value="" id=text3 name=text3><p>  
	<input type="button" value="Set Z-Index" id=button1 name=button1 onclick="setindex()">  
	<DIV id=div1 name=div1 style="width:200;height:200;background-color:lightblue;  
	position:absolute;left:350;top:250;z-index:">DIV</DIV>  
	<select id=select1 name=select1 style=";position:absolute;left:300;top:400;width=300;z-index:"  
	size=1 >  
	<option>Option1  
	<option>Option2  
	<option>Option3  
	</select>  
	<IFRAME id=iframe1 name=iframe1 src="" scroll=none style="width:100;height:115;position:absolute;  
	left:400;top:300;border-color:green;z-index:5"></iframe>  
	</BODY>  
	</HTML>

IFRAME 的z-index被设置成一个不变的值5. 当你输入一个比任何元素都大的值的时候DIV元素还是一直在最下面, 因为他是非窗口类的, 其他的元素都会在DIV元素之上. 当你把SELECT元素的z-index值设的比5大的时候, SELECT元素就会在IFRAME之上. 当你把SELECT元素的z-index值设的比5小的时候, 它就会在IFRAME之下了.  
  
当你把SELECT元素的z- index值设为5, IFRAME会在SELECT元素之上, 因为IFRAME是最后的元素, 因此, 它就会比SELECT优先. 如果SELECT元素在IFRAME后面, 那么在z-index值相同的时候, 它就会在IFRAME之上了.  
  
在Internet Explorer 5.5中Z-index是如何工作的  

在Internet Explorer 5.5中, z-index 被带到了一个新的水平. IFRAMEs不再是窗口类元素. 更多的相关信息请到以下地址查阅"Windowless IFRAME Elements"标题:  

[http://msdn.microsoft.com/workshop/author/dhtml/overview/compat.asp#WindowlessFrames](http://msdn.microsoft.com/workshop/author/dhtml/overview/compat.asp#WindowlessFrames)  
  
这使得SELECT元素变成了唯一的窗口类元素. 如果你在Internet Explorer 5.5中使用前面的代码, 当你把SELECT 元素的z-index值设的比5大的时候, 它会在IFRAME之上. 当你把SELECT 元素的z-index值设的比5小的时候, IFRAME会覆盖SELECT元, 即使他们都是非窗口类元素. 这就是IFRAME的独特性: 它按照z-index顺序和非窗口类元素排列在一起, 并且还可以按照z-index和窗口类元素排列在一起, 比如在这里和SELECT元素一起.  
  
当你把DIV 元素的z-index值设置的比IFRAME大时 (比如6), DIV会覆盖IFRAME. 这符合我们上面的描述: IFRAMEs是非窗口的, 并且它按照z-index的顺序和其他非窗口类元素排列在一起. 当你设的z-index值和IFRAME相等时 (比如5), 它还是会在DIV之上, 这是因为元素的顺序在起作用. 当你把DIV 元素的z-index值设置为6, 同时使SELECT元素和IFRAME的z-index值为5, 那么SELECT元素将会一直在DIV之上, 因为它是窗口类的元素.  
  
然而, IFRAME会在SELECT之上是因为它在顺序上是最后. 为了避免这样, SELECT元素的z-index值必须比IFRAME大, 或者SELECT元素必须排在最后来保证在z-index值一样的情况下它会在IFRAME 之上. Because of this, z-indexing similar content can be difficult. To work around this, use the following methods:  

* 使用样式表的Style属性在需要的时候隐藏和显示元素.  
* Use DHTML Scriptlets. Although behaviors are usually preferred, this is one instance where scriptlets are preferred.  
* 在Internet Explorer 5.5中, 你可以使用popup对象, 使用它你可以在任何元素之上显示丰富的内容. 这在菜单和工具提示功能上非常有用. 想了解更多, 请在下面的地址查阅"popup Object":  

	[http://msdn.microsoft.com/workshop/author/dhtml/reference/objects/popup.asp](http://msdn.microsoft.com/workshop/author/dhtml/reference/objects/popup.asp)  
  
* 使用非窗口类的ActiveX控件来代替窗口类对象. 不幸的是, 所有ActiveX控件都没有非窗口类的实现.  
  
参考  

想了解更多基于IE的Web开发解决方案, 请访问以下Web站点:  

[http://msdn.microsoft.com/workshop/entry.asp](http://msdn.microsoft.com/workshop/entry.asp)  
  
[http://msdn.microsoft.com/ie/](http://msdn.microsoft.com/ie/)  
  
[http://support.microsoft.com/?scid=http%3a%2f%2fsupport.microsoft.com%2fhighlights%2fiep.asp%3ffr%3d0%26amp%3bsd%3dmsdn](http://support.microsoft.com/?scid=http%3a%2f%2fsupport.microsoft.com%2fhighlights%2fiep.asp%3ffr%3d0%26amp%3bsd%3dmsdn)  

________________________________________  

应用于  

* Microsoft Internet Explorer 6.0 Service Pack 1  
* Microsoft Internet Explorer 5.5 Service Pack 2 and Internet Tools  
* Microsoft Internet Explorer 5.0  
  
关键字: kbbug kbdhtml kbfaq kbieobj kbinfo KB177378
