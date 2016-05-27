---
date: 2005-10-20 23:30:52
type: post
title_en: 2005-10-20-build-dokuwiki
title: 架设Dokuwiki
wordpress_id: 162
tags:
- tech
---

现在流行个人门户, 咱也小凑一把热闹. 有了Blog和相册后就是Wiki了.

其实只是想用Wiki来进行一下日常BrainStorm的记录. 在此分享一下架设这个wiki的经验:)

首先说一下, Dokuwiki是使用php开发的轻量级wiki系统. 说它轻量级是因为它不需要专门的数据库系统支持, 它是使用文本文件作为数据源的. 所以只要你的空间支持php, 就基本上可以正常使用Dokuwiki了!

过程是很简单滴^_^

首先到[Dokuwiki的老窝](http://wiki.splitbrain.org/wiki:dokuwiki)下源程序, 然后解压缩, 上传到你的空间.

完事儿以后, 你可以试着访问一下. 如果你的域名为www.abc.com, 你的wiki程序放在wiki目录下, 那么你就是需要访问http://www.abc.com/wiki

这时可能会出现一个错误, 不过不要担心, 你只需要在你wiki目录下的data目录中建立一个名为changes.log的空白文件就ok了!

这个时候, 你的wiki已经可以使用了! 你可以试着写一些东西, 这里有[一篇翻译好的dokuwiki语法说明](https://bbs.ilc.edu.tw/wiki/wiki:syntax).

默认装好的wiki系统的用户界面是英文的, 如果你不习惯的话, 可以通过修改配置文件来更换.

这里就有些不方便了. dokuwiki没有一个方便的后台管理界面, 我们只能通过修改配置文件来达到配置的目的.(哪位达人有时间来写一个简单的后台程序?)

打开conf目录下的dokuwiki.php文件, 把下面这行引号中的值改为zh

	[code lang="php"]
	$conf['lang']        = 'en';              //your language
	[/code]

这样就加载了简体中文的用户界面. 同样的方法可以修改其他的配置, 这个文件中的注释写的还是很详细的.
