---
date: 2006-02-28 10:45:51
type: post
title_en: 2006-02-28-config-the-emacs-for-python-dev
title: 简单配置了一下Emacs, 用于Python开发
wordpress_id: 222
tags:
- tech
---

![Python](http://www.vanille.de/images/python.png)

昨天下载了Emacs 23 Unicode 版本, 今天就配了一下环境, 以便用于Python的开发.

1. 解压Emacs 23 Unicode

	将昨天的[Emacs 23 Unicode版本](http://lab.nickcheng.com/software/Emacs23-20051105-win32.rar)解压到自己的喜欢的目录

2. 下载Python-Mode的配置文件.

	这个配置文件是SourceForge上的一个项目, 所以我们直接去那里下载就可以了, 不过我是半天没有上去, 估计是被GFW(shit)了. 费了半天劲, 最后用TorPak才得以勉强访问. 50多K的一个zip费了我半天劲! 为了不让大家也同样受苦, 在这里放出这个下载

	[Python-Mode配置下载](http://lab.nickcheng.com/software/python-mode.zip)

3. 安装配置包

	Python-Mode的zip包里有4个文件. 先別管都是干嘛的了, 我是一股脑的都放到emacs的site-lisp目录下了. 然后运行bin目录下的runemacs.exe启动Emacs, 用下面的命令检查包是不是放好了.

		M-x locate-library RET python-mode RET

	RET就是回车的意思了!

4. 更改配置文件

	默认Emacs的配置文件在这个位置:

		%userprofile%\Application Data\.emacs

	如果没有的话可以新建一个, 然后输入下面的代码

		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		;;; Python设置
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		(setq auto-mode-alist
		(cons '("\\.py$" . python-mode) auto-mode-alist))
		(setq interpreter-mode-alist
		(cons '("python" . python-mode) interpreter-mode-alist))
		
		(autoload 'python-mode "python-mode" "Python editing mode." t)
		
		(global-font-lock-mode t)
		(setq font-lock-maximum-decoration t)
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		;;; 设置结束
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		;;; 字体设置
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		(setq default-frame-alist
		(append
		'((font . "-*-Lucida Console-normal-r-*-*-13-*-*-*-c-*-fontset-most"))
		default-frame-alist))
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		;;; 设置结束
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		;;; 启动最大化窗口设置
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		(defun w32-restore-frame ()
		"Restore a minimized frame"
		(interactive)
		(w32-send-sys-command 61728))
		(defun w32-maximize-frame ()
		"Maximize the current frame"
		(interactive)
		(w32-send-sys-command 61488))
		;;; Maximum Windows Frame
		(w32-maximize-frame)
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		;;; 设置结束
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

	这里我配置了.py关联python-mode, 语法高亮, Lucida Console的字体(我喜欢的等宽字体), 最大化窗口

	存盘, 重新启动Emacs

	基本上已经可以使用了!
