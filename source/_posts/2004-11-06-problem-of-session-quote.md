---
date: 2004-11-06 05:02:00
type: post
title_en: 2004-11-06-problem-of-session-quote
title: Session引用的问题
wordpress_id: 91
tags:
- tech
---

	// 如果按照以下这样的方式得到Session中存储的对象, 得到的其实是一个引用  
	// 如果对myDataSet中的值进行修改, Session中的值也会相应的更改  
	// ...  
	myDataSet = (DataSet)Session["dataset"];  
	// ...  
	
	// 所以我们在此要使用Copy()方法, 来得到对象的一个副本  
	// 这样一来, 我们在更改myDataSet中的值的时候, Session中的值就不会更改了  
	// ...  
	myDataSet = ((DataSet)Session["dataset"]).Copy();  
	// ...
