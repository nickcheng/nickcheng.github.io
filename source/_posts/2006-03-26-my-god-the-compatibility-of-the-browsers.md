---
date: 2006-03-26 00:00:23
type: post
title_en: my-god-the-compatibility-of-the-browsers
title: 令人郁闷的浏览器兼容性
wordpress_id: 246
tags:
- tech
---

![spring](http://static.flickr.com/21/117638788_b3b1f95856_o.jpg)

虽然W3C有定义Web的标准, 但是W3C并不是浏览器制造商, 更不是主流浏览器的制造者, 所以市面上的各个浏览器都或多或少的不能很好的兼容Web标准, 这就造

成了Web开发者在开发的时候的巨郁闷无比......而我, 就是一个受害者......

在这个改版的时候, 我就遇到了一个兼容性问题. 就是这个div做成的3列框架中的中间的div在IE下会跑到屏幕的最下面(FF和Opera下都是好的). 改了半天CSS,

最后通过Google才发现, 这原来是IE的bug(我就认为是bug, 参考文档在这里: [http://blog.iyi.cn/start/2005/04/widthheight.html](http://blog.iyi.cn/start/2005/04/widthheight.html))!

今天在LP家, LP给我留言, 突然发现留言页面的留言框也跑到屏幕的最下方了. MMD, 晚上回家一看, FF下也没有问题, 看来还是兼容性的问题. 没办法, 先将就

着改了CSS中的一个值, 这才好起来, 要不LP又要让我改版了...=_="

看来, 在做Web开发前, 要好好研究一下这个兼容性的问题了!

ps. 好多WP的Theme的作者似乎都爱用FF, 所以有很多的Theme在IE下都会有些问题, 大家使用的时候注意在IE下看看效果!
