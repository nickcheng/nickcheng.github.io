---
date: 2006-12-11 23:46:27
type: post
title_en: 2006-12-11-begin-with-wpfe-vs-template-and-intellegent-hint
title: 开发WPF/E初步(VS模板+智能提示)
wordpress_id: 318
tags:
- tech
---

WPF/E是微软新一代的Web表现技术, 在我看来, 主要的目的就是和Flash抢地盘! 这下大家有点数了吧:)

在此不准备介绍什么是WPF/E了, 这些东西以后慢慢说, 这篇文章的目的是一个mark, 方便我日后使用:)

在VStudio下开发WPF/E的应用程序还没有自带的项目模板, 安装WPF/E SDK的时候有一个模板, 不过那个模板是Web Project的模板, 用起来麻烦的要死, 这里提供Web Site的模板, 方便多了!
[WPFEApplication.zip](http://www.box.net/public/iaf7o5fts1)

点上面的按钮可以下载模板, 下载好以后放到"[My Documents]\Visual Studio 2005\Templates\ProjectTemplates"目录下面, 这样你在VStudio里新建一个项目的时候就可以看到WPFEApplication的项目模板了^_^

这个模板是我修改别人的, 原文见: [WPF/E: Setting up your workstation for development](http://nickcheng.com/WPF/E: Setting up your workstation for development )

另外再说说在VStudio里写xaml代码.

目前, 在VStudio中编辑xaml有两种方式, 一种是使用WPF Designer(Cider), 好处是可以一边写代码一边在分割的窗口中看到实时的效果, 坏处是WPF的好多特性是WPF/E所不支持的:( 所以写完了还要再单独的调试!

另一种是使用XML Editor来进行编辑, 虽然这样不能实时看到效果, 但也可以自己打开浏览随时查看效果, 而且这样的效果是正儿八经的最终效果! 这很合我的胃口:) 不过目前XML Editor的智能提示不支持xaml的那些标签! 所以我们需要自己动手来丰衣足食!

复制"_C:\Program Files\Microsoft SDKs\WPFE\Help\XSD_"下的"wpfe.xsd"文件到"_D:\Program Files\Microsoft Visual Studio 8\Xml\Schemas_"下. 可能你的安装目录和我会有一些不同, 找到对应的目录就对了! 这时你再在VStudio中打开你的xaml文件, 哈哈, 标签都支持了!
