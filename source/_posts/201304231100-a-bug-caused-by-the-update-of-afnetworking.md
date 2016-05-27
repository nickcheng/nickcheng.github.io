---
date: 2013-4-23 11:08
title: AFNetworking 更新导致的 bug
title_en: a-bug-caused-by-the-update-of-afnetworking
tags:
- tech
- iOS
- afnetworking
- development
- bug
---

昨天调试 [NCMusicEngine](https://github.com/nickcheng/NCMusicEngine) 的时候发现了一个 bug. 调试了半天才发现是引用的 [AFNetworking](https://github.com/AFNetworking/AFNetworking) 模块新版本的更新引入的一个新功能导致的.

之前在 [AFNetworking](https://github.com/AFNetworking/AFNetworking) 里 cancel 掉一个 operation 是没有其他额外的影响的, 但是新版本里, operation 的 cancel 操作会导致 `CompletionBlockWithSuccess` 的 failure. Error Code 是 -999.

所以在更新了 [AFNetworking](https://github.com/AFNetworking/AFNetworking) 后, 如果之前的代码里有对 operation 的 cancel 操作, 那就要注意这一点了.

Github 上这个新功能的 pull request: <https://github.com/AFNetworking/AFNetworking/pull/693>