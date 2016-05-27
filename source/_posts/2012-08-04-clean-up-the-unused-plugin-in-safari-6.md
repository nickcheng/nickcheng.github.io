---
date: 2012-08-04 12:44:13
type: post
title_en: clean-up-the-unused-plugin-in-safari-6
title: 清除 Safari 6.0 中无法使用的插件
wordpress_id: 608
tags:
- tech
- macos
- ml
- mountain lion
- plugin
- safari
---

自从系统升级到 Mountain Lion 以后, Safari 也随之升级, 功能强大了不少. 但随之而来的插件兼容性问题也来了.

Omnibar, TabSwitching 这些插件都用不了了. 而且每次启动 Safari 的时候还总是报错. 所以需要清理一下了.

一般来说, Safari 的插件是在如下两个目录中:

* /Library/Internet Plug-Ins/
* /Users/yourusername/Library/Internet Plug-Ins/

但是奇怪, 清理了上述两个目录中的插件后, 启动 Safari 还是会有插件报错. 经过深入了解, 才知道还有一个目录需要清理:

* /Library/Application Support/SIMBL/Plugins/

这次好了, 终于清理干净了. 如果有人遇到同样的问题, 也可以试试.
