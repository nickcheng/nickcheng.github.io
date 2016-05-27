---
date: 2005-02-22 18:16:00
type: post
title_en: how-to-send-email-through-emacs
title: 如何使用emacs发送邮件
wordpress_id: 107
tags:
- tech
---

主要有两点:

1. 设置 sendto-domain
2. 设置 gnus-post-style 中 address 在[发邮件]时为真实的email.

配置文件如下:

	(require 'smtpmail)
	(setq smtpmail-debug-info t)
	(setq send-mail-function 'smtpmail-send-it)
	(setq message-send-mail-function 'smtpmail-send-it)
	(setq smtpmail-default-smtp-server "smtp.163.com")
	(setq smtpmail-smtp-server "smtp.163.com")
	(setq smtpmail-local-domain "163.com")
	(setq smtpmail-sendto-domain "163.com") ;; maybe
	(setq smtpmail-auth-credentials ; or use ~/.authinfo
	'(("smtp.163.com" 25 "usr" "pwd")))
	(setq smtpmail-starttls-credentials
	'(("smtp.163.com" 25 nil nil)))
	(setq gnus-posting-styles
	'((".*"
	;; default
	(name "Kyle Lee")
	(address "j4v4r_at_163_dot_com")
	(signature-file "~/.sig"))
	("^nnml:mail.*" ;; 被我简化了的过滤规则
	;; misc mail
	(signature-file "~/.sig")
	(name "Kyle")
	(address "javar@163.com")))) ;; real address
