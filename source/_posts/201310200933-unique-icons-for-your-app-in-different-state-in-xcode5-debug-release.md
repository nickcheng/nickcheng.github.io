---
date: 2013-10-20 9:33
title: 在 Xcode 5 下让你的应用在不同状态(debug, release)有不同的图标
title_en: unique-icons-for-your-app-in-different-state-in-xcode5-debug-release
tags:
- tech
- iOS
- development
- config
- compile
- xcode
---

应用在发布到 App Store 之前, 大家都会把应用通过 Ad Hoc 形式发给内部人员进行小范围的测试, 我们把应用的这个状态称为 Staging. 这些人员大多都没有参与过应用, 目的是用来模拟真实用户的操作行为和流程, 以此来找到一些更不容易发现的 Bug.

前段时间我们在准备发布 [NextDay 4.0](https://itunes.apple.com/app/nextday/id491352621?mt=8) 的时候, 也是这样. 但问题也随之而来了. 大家的 iPhone 上都装有 App Store 版本的 [NextDay](https://itunes.apple.com/app/nextday/id491352621?mt=8), 内部测试的 Ad Hoc 版本装上去以后, 图标与名字都和正式版一样, 很难区分. 而我自己的手机上还有 Debug 版本的应用, 这一下就三个了.

所以我就花时间找了一些方法来让不同版本 (不是版本号, 是 Debug, Staging, AppStore 这样的版本) 的同一个应用有各自不同的 Icon 和名字. 这样就避免了上面碰到的问题. 在这里记录一下, 一个是自己备忘, 另外还可以分享给大家:)

# 准备工作

首先, 不同版本的应用要有不同的 Bundle ID. 这里推荐 [Simon Wolf](http://swwritings.com) 的命名方式. 如果你的应用原来的 Bundle ID 是 `com.mycompany.myapp`, 那么这几个版本你可以这么命名:

* `com.mycompany.myapp.debug` Debug (Alpha) 版本
* `com.mycompany.myapp.adhoc` Staging (Ad Hoc, Beta) 版本
* `com.mycompany.myapp` App Store (Production) 版本

然后对应的 Provisionng Profile 也都要准备好. 不用我说了吧.

接下来准备几个不同的图标. 我是用 [Curtis Herbert](http://blog.consumedbycode.com/) 修改的 [PSD 文件](https://s3.amazonaws.com/consumedbycode/downloads/Icons+Template.zip) 做的.  效果可以看我的截图.

![NextDay in different version](http://nickcheng-blog.u.qiniudn.com/20131020/01.PNG)

原始 PSD 来自 [appicontemplate.com](http://appicontemplate.com). 使用方法也在原网站.

# 设置

接下来就是一步一步的设置了.

## Build Configurations

首先是添加 Configurations, 位置见下图所示. 项目之前已经有了 Debug 和 Release 两个配置, 可以分别对应咱们的 Debug 版本和 App Store 版本. 所以咱们只添加一个 Staging 版本就可以了. 我为了能让添加的版本按字母序排列在 Debug 和 Release 中间, 用的名字是 "ForBeta".

![](http://nickcheng-blog.u.qiniudn.com/20131020/02.png)

这步完成后, 你会在 Build Settings 里看到所有的设置都有了三个子选项, 分别对应三个不同的 Configuration.

## Schemes

然后, 我们在项目里需要有两个 Scheme. 这两个 Scheme 在 Debug 时候的行为是一样的, 但在 Archive 的时候, 一个用于 Staging 版本发布内部测试, 一个用于 App Store 发布. 

Scheme 的设置入口在菜单上: "Product" -> "Scheme" -> "Manage Schemes". 我的两个 Scheme 命名如图: 

![](http://nickcheng-blog.u.qiniudn.com/20131020/03.png)

对应 App Store 的 Scheme 设置里, Run 和 Test 的 Build Configuration 都使用 Debug, Profile 和 Archive 使用 Release.

对应 Staging (Beta) 的 Scheme 设置里, Run 和 Test 也用 Debug, Profile 和 Archive 使用 ForBeta.

![](http://nickcheng-blog.u.qiniudn.com/20131020/04.png)

![](http://nickcheng-blog.u.qiniudn.com/20131020/05.png)

有了这里的设置, 咱们就可以通过切换 Scheme 来 Archive 出分别用于 Ad Hoc 发布和 App Store 发布的 App 了.

## App Icon

接着就是 Icon. 现在大家应该都用 Xcode 5 了吧! 既然用了, 那就多用用新功能, Icon 设置这块我使用了 Media Assets. 如果你的老项目还没有启用, 那就麻烦你在对应 Target 的 General 下启用一下.

在 Media Assets 中 (在项目中的默认名字应该是 Images.xcassets), 点击菜单 "Editor" -> "New App Icon", 建立两个新的 App Icon, 分别对应 Debug 和 Staging 版本. 然后把之前准备好的图标分别拖进去. 如图:

![](http://nickcheng-blog.u.qiniudn.com/20131020/06.png)

设置好 Media Assets 后, 还要在对应 Target 的 Build Settings 里分别设置不同版本使用不同的 App Icon. 如图:

![](http://nickcheng-blog.u.qiniudn.com/20131020/07.png)

这样设置好, 不同版本的应用就拥有了各自不同的图标了.

## Bundle ID

再下来就是按照我们前面定义的 Bundle ID 和各个版本的对应关系来进行设置了.

我们需要在 Build Settings 中定义一个变量. 入口在: "Editor" -> "Add Build Setting" -> "Add User-Defined Setting".

![](http://nickcheng-blog.u.qiniudn.com/20131020/08.png)

然后在对应 Target 的 Info 里把 Bundle ID 设置为我们刚才定义的变量.

![](http://nickcheng-blog.u.qiniudn.com/20131020/09.png)

这样, 项目在使用不同的配置文件编译的时候就能分别利用不同的 Bundle ID 了.

## App Name

设置了图标, 如果觉得有必要把应用名称也顺便区分一下的话, 也是可以的.

我们需要在 Build Settings 中再定义一个变量. 比如我是这么定义的:

![](http://nickcheng-blog.u.qiniudn.com/20131020/10.png)

然后在应用名称的设置那里使用这个变量:

![](http://nickcheng-blog.u.qiniudn.com/20131020/11.png)

经过上面的一系列设置, 我现在在 Xcode 里只需要在左上角简单切换一下 Scheme 就可以很方便的编译出各个我需要的应用版本. 妈妈再也不用担心我发布应用了!

# 参考

* [How to Have Two Versions of the Same App on Your Device](http://nilsou.com/blog/2013/07/29/how-to-have-two-versions-of-the-same-app-on-your-device/)
* [Unique icons for debug, beta, and App Store builds in Xcode 5](http://blog.consumedbycode.com/unique-icons-for-debug-beta-and-app-store-builds-in-xcode-5)
* [Concurrent Debug, Beta and App Store Builds](http://swwritings.com/post/2013-05-20-concurrent-debug-beta-app-store-builds)