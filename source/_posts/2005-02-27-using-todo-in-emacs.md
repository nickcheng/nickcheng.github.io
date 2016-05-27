---
date: 2005-02-27 11:23:00
type: post
title_en: using-todo-in-emacs
title: 在Emacs中使用TODO
wordpress_id: 108
tags:
- tech
---

	(setq todo-file-do "~/todo/do")  
	(setq todo-file-done "~/todo/done")  
	(setq todo-file-top "~/todo/top")  

上面的内容写在.emacs文件中, 然后建立上面指定的目录(~/todo/)  
  
然后在Emacs中 `C+x C+f`, 切换到todo目录, 键入 `do`, 回车. 这样, 我们就建立了do文件  
  
接着, 我们要在do文件中建立我们的category  

	M+x todo-add-category  

输入一个分类的名称(我输入了Personal)  

这时, 你会看到屏幕上显示一些看似乱七八糟的东西, 不要理会这些, C+x C+s保存之  
  
好, 下面我们切换到todo mode    

	M+x todo-mode  

好了, 我们可以开始安排我们的todo了!  
  
附:  

>i 加入一个条目  
e 编辑条目  
k 删除条目  
+/- 在不同category之间切换  
j 跳转到某个category  
f 对已完成的事件归档，可以加入评论  

:)
