---
date: 2014-6-10 15:36
title: Xcode 5 编译自动增加版本号
title_en: auto-increase-version-number-in-xcode-5
tags: 
- tech
- xcode
- development
- iOS
- compile
- config
---

为了让自己的应用显得更专业, 我决定把项目的 Build 号整成自动增加的. 为了免除我的操心, 我就让他在我每次编译的时候把 Build 号加一. 就好像这个样子.

![Build Number](http://nickcheng-blog.u.qiniudn.com/20140610/build-number.png)

设置方法很容易. 先在项目的 "Build Phases" 里添加一项.

![Step 1](http://nickcheng-blog.u.qiniudn.com/20140610/1.png)

选择添加 "Run Script" 

![Step 2](http://nickcheng-blog.u.qiniudn.com/20140610/2.png)

然后你可以在红框位置把名字给改了. 不过这不重要, 重要的是橙框里的内容!

![Step 3](http://nickcheng-blog.u.qiniudn.com/20140610/3.png)

脚本如下:

```
buildNumber=$(/usr/libexec/PlistBuddy -c "Print CFBundleVersion" "${PROJECT_DIR}/${INFOPLIST_FILE}")
buildNumber=$(($buildNumber + 1))
/usr/libexec/PlistBuddy -c "Set :CFBundleVersion $buildNumber" "${PROJECT_DIR}/${INFOPLIST_FILE}"
```

基本原理就是把你原本的 "Build" 里那个数取出来然后加一再放回去. 对了, 你原本的 Build 里如果是 "1.0" 要改为 "1", 不然会报脚本错误的.

最后一点要注意的就是这个新添加项的位置. 上图可以看到, 我是放在 "Link Binary..." 和 "Copy Bundle..." 中间的.

到这里你就可以试试编译, 看看效果了.