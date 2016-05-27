---
date: 2007-02-05 00:48:30
type: post
title_en: change-the-face-of-emacs-20070205
title: 给Emacs改了一个样子
wordpress_id: 335
tags:
- tech
---

一直以来, 自己写代码的环境都是黑色背景的! 也许和最早使用的GWBasic有关系吧:) 但是目前电脑上的Emacs一直还没有配成黑色背景(最近少写代码了?), 今天狠狠心给配了一下, 又把字体给改小了一号! 发现自己还是喜欢小字体, BT啊! 真不知道如果以后显示器再大下去, 我是不是还能继续保持这个习惯!

废话少说, 贴代码了!

	;; 字体设置
	(create-fontset-from-fontset-spec "-outline-Bitstream Vera Sans Mono-normal-r-*-*-10-97-96-96-c-*-fontset-chinese")
	(set-fontset-font "fontset-default" nil
			  "-outline-新宋体-*-r-*-*-12-*-96-96-c-*-iso10646-1" nil 'prepend)
	(set-fontset-font "fontset-chinese" 'kana
			  "-outline-新宋体-*-r-*-*-12-*-96-96-c-*-iso10646-1" nil 'prepend)
	(set-fontset-font "fontset-chinese" 'han
			  "-outline-新宋体-*-r-*-*-12-*-96-96-c-*-iso10646-1" nil 'prepend)
	(set-fontset-font "fontset-chinese" 'cjk-misc
			  "-outline-新宋体-*-r-*-*-12-*-96-96-c-*-iso10646-1" nil 'prepend)
	(set-fontset-font "fontset-chinese" 'symbol
			  "-outline-新宋体-*-r-*-*-12-*-96-96-c-*-iso10646-1" nil 'prepend)
	(set-default-font "fontset-chinese")
	
	;; 颜色设置
	(setq frame-background-mode 'dark)
	(set-background-color   "black")
	(set-foreground-color   "gray")
	(set-cursor-color   "yellow")

再附赠一个高亮光标所在行的设置:)

	;; 高亮光标所在行设置
	(require 'hl-line)
	(global-hl-line-mode t)


