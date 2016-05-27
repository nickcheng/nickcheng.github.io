---
date: 2006-03-10 16:48:26
type: post
title_en: 2006-03-10-the-fucking-bad-rss-format-source
title: 不规则的RSS害死人啊
wordpress_id: 237
tags:
- tech
---

![image](http://static.flickr.com/49/110396274_28438e4050.jpg)

今天在做一个RSS Parser, 在测试的时候突然程序抛出一个异常, 说是区域代码不正确. 查了一下数据源, 又看了一下文档, 发现了问题.

大家看图, 高亮部分是这个rss源的language一节的内容, 乍一看似乎没什么问题, 就是表示地区是中国, 但是一查文档, 就发现了问题!

> 区域性名称遵循 RFC 1766 标准，格式为“languagecode2-country/regioncode2”，其中 languagecode2 是从 ISO 639-1 派生的由两个小写字母构成的代码，country/regioncode2 是从 ISO 3166 派生的由两个大写字母构成的代码。例如，美国英语为“en-US”。在双字母语言代码不可用的情况中，将使用从 ISO 639-2 派生的三字母代码；例如，三字母代码“div”用于使用 Dhivehi 语言的区域。某些区域性名称带有指定书写符号的后缀；例如“-Cyrl”指定西里尔语书写符号，“-Latn”指定拉丁语书写符号。

看到这些, 我顿悟! 就是那个下划线的问题! 没办法, 不和规范的数据肯定会有, 咱们只能做适配了:(

我妥协......