---
date: 2006-10-30 14:11:16
type: post
title_en: 2006-10-30-upgrade-wordpress-to-205
title: Wordpress升级到2.0.5
wordpress_id: 303
tags:
- life
---

[WordPress又升级了](http://wordpress.org/development/2006/10/205-ronan/), 这次的名字不再是Jazz音乐家的名字了, 而是作者自己刚出生的儿子的名字--Ronan. 幸福的小家伙:)

升级以后, 发现自己网站的内容全变成了???, 估计又是哪个字符编码的问题. 仔细回想了一下, 自己第一次在BlueHost上安装WordPress的时候, 曾经修改过程序, 而这次升级覆盖了之前我修改的文件, 所以还得自己再修改一下:) ok, 问题找到, 开始解决!

参考之前自己[参考过的那篇文章](http://tao.kaoart.info/cms-software-doc/wordpress-about/kunstao/2006/554/).

打开wp-includes/wp-db.php文件, 在56行添加
$this->query("SET NAMES 'utf8'");

添加后的样子就是:

	}
	$this->query("SET NAMES 'utf8'");
	$this->select($dbname);
	}

搞定以后上传覆盖文件, 再打开[自己的网站](http://nickcheng.com), 哈哈...好了!!!
