---
date: 2008-04-10 11:38:01
type: post
title_en: some-ticks-in-ie-web-developing-1
title: IE下Web开发注意事项 - 1
wordpress_id: 431
tags:
- tech
- develop
- ie
- web
---

最近因为要做一些Web开发工作, 所以天天都是纵横在XHTML, CSS和Javascript的海洋中. 要说这些工作还是蛮有趣的, 但如果遇到浏览器兼容问题, 那就郁闷的很了.

所谓浏览器兼容问题, 就是你设计好的一个页面, 在FX(Firefox)下看的是好好的, 漂亮的, 但是换到IE下看, 就变的歪七扭八, 乱七八糟的了. 究其原因, 无非是各个浏览器之间没有遵循一个统一的标准. 这可好, 苦了我们做Web开发的了...

前几天就遇到了问题. 一个页面的设计, 在FX(Firefox)下好好的, 但是在IE下就莫名的多了几个空行出来.

看了一下代码, 空行是出在几个DIV之间的. 先检查了这些DIV的margin, padding, border, 都没有问题; 再看这些div之间有没有什么特殊字符, 也没发现. 搜了一下IE和FX的CSS兼容问题, 也没有找到类似的...于是决定自己重现问题再看.

因为原有页面比较大, 我就把出问题的那部分代码抽了出来, 精简了一下, 单独写了一个小HTML文件用来调试. 因为IE下没有Firebug这么好用的实时改变代码就能看到效果的工具, 我就只能改一下, 再在IE中看一眼. 终于, 被我发现了问题.

问题不是出在那几个产生空行的DIV身上, 而是出在他们的父容器DIV身上. 当我把父容器DIV的宽度(width)由auto改为100%后, 那几个DIV之间的空行就都消失了. 其实这也不单单是父容器的问题, 因为如果你只是简单写几个DIV, 父容器就算不指定宽度, 里面的DIV也不会出现空行. 这个问题另外的触发条件是那几个产生空行的DIV使用了浮动(float)布局, 并且还使用了clear:both消除浮动, 这一来一去之中就造成了我遇到的问题.

OK, 问题解决了, 那就总结一下吧.

**当DIV之间莫名出现空行时, 要看看这些DIV是否使用了浮动布局, 并在其中使用了clear:both消除浮动, 如果是这样, 那就请修改这些DIV的父容器DIV的宽度为固定(固定数值或固定百分比), 说不定会解决你的问题哦:)**

ps. 不想在这里说哪个浏览器好, 哪个浏览器坏. 各公司的产品肯定都有各自的设计和各自的理由. 不论一个东西做的再好再坏, 只要你在统计报表里看到有大量的人在用, 为了用户, 那你只能乖乖的去想办法包容一切, 不然你就可能丧失一部分用户. 与其在那儿抱怨, 不如用这时间去帮忙擦擦屁股, 虽然恶心点儿, 但我也忍了......对了, 我现在用FX 3.0b5挺爽的, 速度快, 每天还能crash一两次......
