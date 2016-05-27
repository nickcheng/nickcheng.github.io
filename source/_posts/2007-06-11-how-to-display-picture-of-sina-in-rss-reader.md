---
date: 2007-06-11 13:25:45
type: post
title_en: 2007-06-11-how-to-display-picture-of-sina-in-rss-reader
title: 让新浪显示图片-突破新浪图片屏蔽
wordpress_id: 367
tags:
- tech
- anti
- pic
- refer
- sina
---

先说一句, sina太SB了, 竟然想出这样的方法, BS啊1000遍!

先说解决方法. 最简单的方法就是在Firefox中, 在地址栏中输入about:config, 然后修改network.http.sendRefererHeader的值为1. 这样就ok了, 现在可以立刻试试, 不需要重新启动Firefox.

方法的原理很简单. 就是不发送referer header, 这样sina就无法判断你是在哪里访问他了, 他就会乖乖的给你显示他的图片!

不过不发送referer header也有弊端. 有的下载网站在下载的时候是要看referer header的, 这样一来, 你就不能下载了.

为了让事情更完美, 俺又找到了[这个Firefox的插件](http://labs.beffa.org/sendreferer/).

安装了这个插件以后, 就不用我之前说的那个简单的方法了. 插件会修改sendRefererHeader的值为0, 这保证了不发送referer header; 同时插件还提供了打开某个链接同时发送refer header的功能, 这样一来, 需要下载的时候就只需在链接上点右键,选择"Open link with referer header"就行了!

虽然事情被sina弄得很复杂, 但是有了Firefox, 还是美好的:) 最起码, 我的GoogleReader可以显示朋友sina博客的图片了!

但我还是要强烈建议大家不要用sina的博客!
