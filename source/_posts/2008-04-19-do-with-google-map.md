---
date: 2008-04-19 01:23:10
type: post
title_en: do-with-google-map
title: 折腾Google Map
wordpress_id: 432
tags:
- tech
- google
- map
---

因为在中国, GoogleMap有ditu和map之分, 所以我要折腾!

gmap在中国的地图服务是和mapabc公司合作的, 既然是国内的公司, 走的自然是国内路线, 那么全球的gmap走的自然就不是国内路线. 正因为这点不同, 同时又因为各国使用的地理坐标系不同, 所以导致了gmap在中国和全球的不同. 举一个明显的例子就是你在ditu.google.com看到的一个地方的坐标和google earth上是不一样的.

因为找不到不同坐标系之间的对照关系, 所以不能用算法来进行转换, 只好使用黑盒的方法, 使用偏移值来修正. **在google earth上和ditu.google.com上找到同一个点的经纬度信息, 计算他们之间的差值, 然后利用这个差值再来修正这两者数据的不同.** 但要注意的是, 这个误差不是线性的, 所以不能一劳永逸, 你把北京的修正值拿到上海, 修的就不那么正了, 所以, 这个基本上要每个城市都要保存一个修正值...囧

我这里有一个北京的修正值, 需要的可以拿去先用.

> ditu - earth:
Lat: 0.001444
Lng: 0.006203

ps. 调试的时候出现了卫星图不可用的情况, 也不知道是被GFW还是服务有问题. 看来如果应用严重依赖地图的话, 使用GoogleMap并不是一个好方法, 最好还是能有自己的地图系统(GIS)

ps2. 顺便鄙视一下sql server, 浮点转字符串默认只有6位, 如果使用8位和16位的style转换, 出来的是科学计数法, 怎么就这么麻烦呢?