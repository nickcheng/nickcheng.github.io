---
date: 2005-10-11 12:52:12
type: post
title_en: some-problems-in-using-ftp-component-of-xceed
title: 在使用Xceed的FTP组件时遇到的问题
wordpress_id: 51
tags:
- tech
---

最近在做的东西用到了Xceed的FTP组件。在使用的时候遇到了一个小问题，如下：

	The FtpClient is in an unexpected state.
	Xceed.Ftp.FtpInvalidStateException: The FtpClient is in an unexpected state.
	at Xceed.Ftp.FtpClient.CheckState(FtpClientState expectedState)
	at Xceed.Ftp.FtpClient.Disconnect()
	at McasFileProcessor.Helper.BossHelper.UploadFile() in f:\code\vss\3-developi
	ng\161_v2\misc\mcasfileprocessor\helper\bosshelper.cs:line 491
	at McasFileProcessor.FileProcessor.ToBoss(String[] args) in f:\code\vss\3-dev
	eloping\161_v2\misc\mcasfileprocessor\fileprocessor.cs:line 53
	at McasFileProcessor.Program.Main(String[] args) in f:\code\vss\3-developing\
	161_v2\misc\mcasfileprocessor\program.cs:line 34

这是在Disconnect的时候，组件抛出的一个异常。

一开始我还以为是自己程序的问题，后来到[官方论坛](https://www.xceedsoft.com/Forums/ShowForum.aspx?ForumID=29)查了一下，才发现这是1.0版本组件的问题，[详细的内容在这里](https://www.xceedsoft.com/Forums/ShowPost.aspx?PostID=1711)。

简单的说，就是在我们Disconnect之前，Socket自己就已经关闭了，所以产生了这个异常。据说2.0时就不会再抛出这个异常了。
