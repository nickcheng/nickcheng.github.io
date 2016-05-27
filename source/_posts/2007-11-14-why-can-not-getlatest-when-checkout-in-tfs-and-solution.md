---
date: 2007-11-14 15:15:11
type: post
title_en: why-can-not-getlatest-when-checkout-in-tfs-and-solution
title: 关于TFS中Checkout不会自动Get Latest的解释和解决方法(图文)
wordpress_id: 424
tags:
- tech
- solution
- tfs
---

**原因**

TFS中, Check Out动作不会自动进行Get Latest的动作, 所以不能保证每次Check Out出来的东西都是最新的. 这个情况看似是个BUG, 但却是TFS的By Design. MSDN Forum中的blog有解释如下: 

1. 假定TFS Server上的代码总是一个完整的可用的Build，也就是说每个员工必须保证你的一个完整的Check In是必须可以Build成功的。

2. 通常意义上，你开始新的工作的时候同样应该确保你的本地版本是可以通过Build的。当然可能是跟Server上最新的版本同步的，也可能是Server上某个时刻的Snapshot，总之是一个好的版本。

3. 当你需要编辑代码的时候，Check out这个动作只是做了个Editable的标记而已。如果发现Server上有新的版本，只是提示你Server上的版本比你的Local版本要新(这个提示在output窗口中显示)，而不是Get Latest Version。为何呢？因为通常意义上来说，如果Server上有一个新的版本，意味着有了一个新的Change Set，而一个Change Set并不是只有一个文件，如果你只是把正要编辑的版本Get Latest Version，由于Code的依赖关系，很可能导致本地编译被Block。

4. 为了避免开发人员陷于此种陷阱，TFS团队决定不是直接Get Latest Version，而是在你完成了代码工作后要Check In的时候告诉你有Conflict,需要再做Merge来。这样在Check In的时候开发人员必须仔细的对比检查，做好Merge工作才能确保在你Check In之后Server上又是一个好的Build。Merge的时候注意千万别把别的开发人员的Code给覆盖了。

微软答应会在TFS的第二版本中会提供是否自动Get Latest的选项。

**解决方法**

既然MS现在没有提供解决方法, 我们只能自己想办法了. 

在Visual Studio的菜单中选择”Tools”->”Macros”->”Macros IDE”, 打开宏编辑器

[![宏编辑器](http://photo11.yupoo.com/20071114/145403_1031657622_m.jpg)](http://www.yupoo.com/photos/view?id=ff8080811638374901163cef9aa54c00)

在Module1中添加如下代码

	    Sub CheckoutLatest()
	        DTE.ExecuteCommand("File.TfsGetLatestVersion")
	        DTE.ExecuteCommand("File.TfsCheckOut")
	    End Sub

要让你那里看到的和我图上的一致, 然后保存关闭. 

这只是增加了宏, 如果每次需要运行的时候都打开宏浏览器, 那就太麻烦了, 所以我们还要给这个宏添加一个快捷键. 

在菜单中选择:”Tools”->”Options”, 然后选择”Environment”->”Keyboard”

[![选项](http://photo5.yupoo.com/20071114/145404_279588783_m.jpg)](http://www.yupoo.com/photos/view?id=ff8080811638374901163cef9cf04c02)

然后在”Show commands containing:”下的输入框中输入”checkoutlatest”, 就能定位到我们新建的宏了. 

在”Press shortcut keys”中输入你希望用的快捷键(我使用的是”Alt-O”), 然后点击”Assign”键, 点击”OK”, 完成. 

[![选项完成](http://photo5.yupoo.com/20071114/145404_248546321_m.jpg)](http://www.yupoo.com/photos/view?id=ff8080811638374901163cef9f2d4c06)

以后, 在需要Check Out文件的时候, 就可以使用快捷键”Alt-O”来操作了, 这个操作可以保证你Check Out到Latest的文件.
