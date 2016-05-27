---
date: 2008-01-03 19:33:22
type: post
title_en: the-final-solution-of-beautifing-fonts-in-windows
title: Windows下的字体美化终极方案
wordpress_id: 427
tags:
- tech
- font
- gdi++
- windows
---

在Windows下觊觎苹果的那种虚虚的字体很久了, 虽然有不少人认为那种字体看起来不爽, 但是我本人还是很喜欢的. 现在我终于可以在Windows下也达到那种境界了!

下面隆重推出今天的主角--GDI++和FreeType! 关于这两个东东是什么的问题, 我就不在此赘述, 大家可以参看[这个链接](http://bbs.themex.net/showthread.php?t=16821991). 我这里主要介绍方案.

使用GDI++和FreeType可以使用类似苹果下的字体渲染技术, 而不是Windows自带的ClearType. 大家可以直接在我的box里[下载打包的好的文件](http://www.box.net/shared/f6mqz090ks). 解压缩到一个目录后, 运行里面的gditray, 立刻你就会看到效果了. 在托盘图标上右键单击还可以打开菜单来切换配置项, 选择预置好的几个配置(也都是我找来的).

哈哈, 看看是不是有些惊艳? 不过还没完......

还需要介绍一个配角给大家, 那就是[蚂蚁定制的丽黑字体](http://www.box.net/shared/5cvnw2tus8). 这个字体是极限论坛的蚂蚁hack的一个版本, 用这个字体可以替换掉系统的宋体, 然后再配合上面的GDI++和FreeType, 那看起来的效果真是绝了, 我喜欢!

下面总结一下步骤:
	
1. 用丽黑字体替换宋体(直接安装覆盖即可, 注意备份原有字体; 如果不行就把原有字体改名然后再安装)
2. 重启系统使新字体生效(大家都这么说, 但我就不用重启)
3. 通过gditray使用GDI++和FreeType.

好了, 就这么简单. 我在Vista下用的, 是不错的, 相信在XP会更容易! 另外配置文件我喜欢那个"细"的效果, 你呢?

Enjoy!
