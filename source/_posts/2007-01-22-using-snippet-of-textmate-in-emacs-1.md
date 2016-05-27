---
date: 2007-01-22 23:01:46
type: post
title_en: 2007-01-22-using-snippet-of-textmate-in-emacs-1
title: Emacs下使用TextMate的Snippets功能(一)
wordpress_id: 328
tags:
- tech
---

最近一直被Mac下的TextMate所引诱^_^ 无奈TextMate在Windows下没有移植, 于是乎, 就翻遍互联网来寻觅Windows上的类似的东西.

功夫不负有心人, 嘿嘿, 昨天说的Intype就是成果之一了! 另外还发现了好东西呢! 那就是Emacs下Snippets的实现.

照理说, Emacs这么强大, 怎么能连这个功能都不能实现呢? 我真应该一开始就朝Emacs这个方向来找!

废话少说, 现去下载最新的Snippet.el, 我们需要的Snippets功能就都在这个文件里了!

[http://www.kazmier.com/computer/snippet.el](http://www.kazmier.com/computer/snippet.el)

下了以后放好, 然后在Emacs中load进来. 到此为止就完成了Snippets功能的加载, 你可以试试在"*scratch*" buffer下输入"M-x snippet-insert 回车", 然后再输入"<a xhref="$$" mce_href="$$">$$</a> 回车". 看到什么了? 是不是很爽的感觉?

要注意哦, 至此我们只是完成了Snippets功能的加载, 而如果要在写代码的时候使用的话, 这还是不够的, 我们还需要对应于各个语言的Bundles. 有了Bundle, 我们才能快捷的输入预设的代码.

关于Bundle的内容稍后再推出:) 别急, 嘿嘿...

ps.
看到这个东东的来源
[http://gugod.org/blog/2006/01/emacs-my-snippetel.html](http://gugod.org/blog/2006/01/emacs-my-snippetel.html)
