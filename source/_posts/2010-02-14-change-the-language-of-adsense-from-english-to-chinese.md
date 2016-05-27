---
date: 2010-02-14 12:43:28
type: post
title_en: change-the-language-of-adsense-from-english-to-chinese
title: 把英文的Adsense广告改成中文
wordpress_id: 505
tags:
- tech
- adsense
- chinese
- language
---

刚整完Blog, 顺手放上了Google Adsense. 浏览了一下, 发现有个小问题, 广告怎么都是英文的呢? 我的又不是英文Blog.

想了一下, 可能是和自己的空间在国外有关, 服务器的IP地址不是中国的. 这Google Adsense投放的广告除了上下文相关以外, 还会考虑各种其他的相关因素, 比如服务器的IP地址所在地, 访问者的IP所在地等等.

好吧, Google了一圈, 找到了一个解决的方法. 只需在Adsense的代码里加上这么一句就可以了

> google_language = 'zh-CN';

放的位置就在"// -->"前面即可.

再看看, 现在广告就都是中文的了:)

更新: 根据Rey的经验, 如果是在中文的AdSense申请的广告代码, 里面应该就已经有了上面的语言代码.
