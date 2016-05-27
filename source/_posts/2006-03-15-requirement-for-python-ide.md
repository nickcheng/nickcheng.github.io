---
date: 2006-03-15 10:10:22
type: post
title_en: requirement-for-python-ide
title: 偶对Python IDE的要求
wordpress_id: 238
tags:
- tech
---

最近给一哥们推荐Python, 在他的要求下, 要找一个适合Python的IDE! 我当然强烈推荐Emacs了! 但是无奈于自己的学艺不精, 好多他要求的功能我都暂时实现不了, 只好再帮他找找其他的了!

总结了一下基本需要的功能

1. 代码高亮. 用颜色区分变量, 类, 数字, 字符串等等
2. 自动完成. 比如我打def+空格, 他会自动出来def ():
3. 智能提示. 在一个类后面打点会自动出现类成员
4. 方便的Debug, 调试
5. 类视图
6. 项目文件列表视图

我再加点补充意见

1. 支持SVN绑定, 最起码要能在IDE里进行基本的SVN操作
2. 类似Emacs的键盘设定, 可以让我手不离开主键盘完成所有操作(上面一排F功能键是可以按的)

发现能达到基本功能的IDE还是蛮多的, 有商业的, 开源的, 跨平台的, Win下的... 不过没时间用那么多种. 简单用了一下Limodou的NewEdit, 感觉已经很不错了, 而且是开源的, 并且作者是中国人, 也是一个非常活跃的Pythoner, 所以, 这个IDE的未来还是很好的, 我就是把这个推荐给哥们的!

至于我自己, 还是以Emacs为主, 不行的时候也用NewEdit.

不过Emacs下配置自动完成和智能提示的效果仍然不是太理想, 再折腾一下吧!

放Link出来, 感兴趣的朋友自己看看, 有问题留言, 大家一起探讨:)

NewEdit: [http://wiki.woodpecker.org.cn/moin/NewEdit](http://wiki.woodpecker.org.cn/moin/NewEdit)

NewEdit用到的WxPython库: [http://wxpython.org](http://wxpython.org) (只下载Runtime就可以了)

Emacs配置相关:
[http://www.bloomington.in.us/~brutt/msf-abbrev.html](http://www.bloomington.in.us/~brutt/msf-abbrev.html)
[http://ecb.sourceforge.net/](http://ecb.sourceforge.net/)
