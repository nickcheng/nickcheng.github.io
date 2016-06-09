---
date: 2015-4-28 15:47
title: Sublime 下写 Markdown 的暂时方案
title_en: write-markdown-in-sublime
tags: 
- tech
- markdown
- sublime
- writing
- life
---
一直都没有找到太合适的写 Markdown 的工具. 虽然尝试过不少, 但仍然没有一个真正习惯的. 其实自己纠结的无非是下面几点:

* GFM 语法. 其中关键是代码块的支持
* 带目录树的 Sidebar
* 暗色颜色主题

最早接触 Markdown 用的是 Mou, 用着用着就觉得功能差太多了, 基本满足不了我.

然后一直间断的用 Ulysses, 从 Ulysses III 到现在改名的 Ulysses for Mac 2.0 他家的三栏是我最喜欢的, 但是他自己独有的一些语法还是让我这个习惯于 GFM 语法的人无法适应. 听说 Ulysses 未来有计划支持 GFM, 那么就等它支持的时候再来试试吧.

脱胎于 Mou 的 Macdown 倒是功能上提升了不少, 而且开源也方便爱好者扩展, 很看好. 但是一直没有支持 Sidebar 目录树的计划. 我自己有一个半截的 Fork, 但一直还没来得及完成, =_=|||

其他一些如 IA Writer, Write Room, Writer Pro 等都不太满意, 就不细说了.

于是最终还是转回到改造常用的 Text Editor. 这个重任就落在 Sublime Text 身上了.

Sublime 的丰富的插件让这一切得以可行, 最终我的配置大概如下:

[修改过颜色配置的 Markdown Light](https://github.com/nvtkaszpir/MarkdownLight)

这家默认的颜色都是亮色调的, 所以我用了这个模仿 Dracula 主题配色的 Fork

[Dracula Theme](https://github.com/zenorocha/dracula-theme)

用到了这个主题的语法配色, 主要是为了让打开其他类型的文件能有统一的体验

[cobalt2](https://github.com/wesbos/cobalt2)

这个是使用的编辑器主题. 主要目的是边栏美化

所以最后我的配置文件中样式相关的部分是这样的, 字体搭配属于附赠:

```json
"color_scheme": "Packages/Dracula Color Scheme/Dracula.tmTheme",
"theme": "Cobalt2.sublime-theme",
"font_face": "InputMonoCompressed Thin",
"font_size": 16.0,
```

不得不提的还有 GitHub 家的 Atom Editor. 可能还是因为发展时间短, 他还是很多小细节的地方不是那么到位, 而且非 Native 的架构用起来的性能还是要比 Sublime 差上一些, 所以暂时还无法委以重任.