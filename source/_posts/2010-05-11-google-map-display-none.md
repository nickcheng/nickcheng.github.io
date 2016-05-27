---
date: 2010-05-11 21:43:16
type: post
title_en: google-map-display-none
title: Google Map - display:none
wordpress_id: 565
tags:
- tech
- display
- div
- google
- hide
- map
- resize
---

使用Google Map时遇到一个问题. 我用Tab控件分别放置Google Map和数据, 当我切换到数据Tab后调整窗口的大小, 然后切换回地图的Tab, 这时, 地图会不见.

原来, 把Google Map放到一个DIV里, 当DIV被设置为"display:none"后, 浏览器会告诉Map API这个DIV的尺寸为0, 这时, API就会把地图的尺寸也设置为0.

解决方法有两个:

1. 如果你的地图尺寸是确定的, 那么在建立地图的时候就指定上尺寸
2. 如果你不确定地图的尺寸, 那么在重新显示地图的时候, 调用一下 map.checkResize() 方法
