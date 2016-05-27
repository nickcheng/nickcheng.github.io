---
date: 2007-05-14 11:17:27
type: post
title_en: 2007-05-14-using-symbian-emulator-in-jre-16-environment
title: 在JRE 1.6环境下使用Symbian模拟器
wordpress_id: 362
tags:
- tech
- java
- jre
- symbian
---

安装完JRE 1.6后, Symbian模拟器可以使用, 不过当使用菜单中的"Utilities"和"Preferennces"时, 出现错误提示"Cannot start ECMT Manager".

出现这种情况是因为Symbian模拟器对新的JRE支持不够的原因. 如果这个时候你卸载新版的JRE, 改装老的JRE 1.4, 那自然是没有问题了. 不过这样实在是太麻烦了, 我在这里介绍一种更方便的方法.

Symbian模拟器对JRE的支持是写在配置文件中的, 所以我们其实只需简单的修改一下配置文件, 让Symbian模拟器支持JRE 1.6即可!

配置文件的位置在:

	<installation_path>\Epoc32\tools\ecmt\config\config.properties

将文件中的"epdt.java.version.start"参数值加上新JRE的版本号即可. 改完以后的这行应该是这样:

	epdt.java.version.start=1.4.1,1.4.2,1.5,5.0,1.6,6.0

改完以后, 再启动你的Symbian模拟器, 原来不能使用的菜单就可以使用了:)
