---
date: 2005-06-16 15:10:00
type: post
title_en: setup-a-wap-server
title: 简单建立一个Wap Server
wordpress_id: 116
tags:
- tech
---

由于工作的关系, 昨天需要建立一个简单的WAP SERVER. WAP网页都是现成的, 我要做的就是发布而已, 很简单!  
  
具体过程如下:  
  
1. 在IIS里建立虚拟目录, 指向要发布的WAP网页.  
  
2. 更改这个虚拟目录的属性, 添加新的MIME  

		.wml text/vnd.wap.wml  
		.wmlc application/vnd.wap.wmlc  
		.wmls text/vnd.wap.wmlscript  
		.wmlsc application/vnd.wap.wmlscriptc  
		.wbmp image/vnd.wap.wbmp  

	这样IIS就可以对以这些扩展名结尾的文件做处理了!  
  
3. 文档里面再添加一个初始页面index.wml, 这样用WAP访问虚拟目录就可以直接定位到index.wml文件了.  
  
好了, 就这么简单! 有Opera的话, 就直接输入地址访问一下看看吧!
