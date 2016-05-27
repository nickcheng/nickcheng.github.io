---
date: 2005-08-06 11:16:00
type: post
title_en: my-foolish-bookmark-list
title: 自己输出的蠢蠢的网摘列表
wordpress_id: 128
tags:
- tech
---

自己虽然都在努力的写着Blog, 但是仍然不能达到每天一篇. 一直看到别人的Blog上有很多都是[del.icio.us](http://del.icio.us/)或者[365key](http://www.365key.com/)的网摘列表, 于是就想自己也来这么一招, 一来可以充实一下我那贫瘠的土地:), 二来也给为数不多的大家Share一下.  
  
不知道别人的网摘都是怎么生成的, 看了一圈, 发现有好多人的都一样. 首先怀疑是不是书签服务商提供了这样的服务, 不过自己简单的搜了一下, 没有发现太明显得地方说这个事情, 也懒得去深入找下去. 然后想是不是某个知名的牛人提供了这样的程序, 然后大家都去用. 既然人家能自己动手, 那我也就自己动动手吧.  
  
本来想是自己写个小程序通过调用del.icio.us的API来生成列表, 不过想到写个Blog还要再开一个程序就觉得麻烦, 就放弃了这个想法. 现在采用的方法巨简单. 因为我查看网页源代码的编辑器是[Editplus](http://www.editplus.com/), 所以我就利用了一下他, 具体步骤如下:  
  
1. 生成自己网摘的简易列表. del.icio.us提供了一个生成自己网摘简易列表的方法, 大家看看[帮助文档](http://del.icio.us/doc/html)就明白了. 我自己用的是这个 [http://del.icio.us/html/nickcheng?extended=body&tags=no&rssbutton=no&count=20](http://del.icio.us/html/nickcheng?extended=body&tags=no&rssbutton=no&count=20)  
2. 查看列表的源文件. 我的是在Editplus中查看得哦!  
3. 使用Editplus的宏功能转换代码. 我自己编辑了一个把列表html源代码转换为我Blog可以使用的代码的宏.  
  
ps. 本来del.icio.us提供的生成简易列表的方法就是输出现成的网摘, 不过他生成的代码我的Blog不能直接使用, 所以有了以上的步骤.  
  
粘贴转换后的代码到自己的Blog, 厚厚, 搞定了! 方法是不是有些蠢? 不过操作起来还是挺简单的. 那个宏编辑好以后就一直用了!  
  
自己的一个想法是:  

修改自己的Blog程序, 在写Blog的时候有一个功能, 可以直接生成网摘, 这样就更简单了.  
  
实现这个想法也不难, 就是通过程序调用del.icio.us的API. 呵呵, 等有时间再说吧, 自己还是比较懒的说. 我的法师才24级了......
