---
date: 2004-11-22 19:47:00
type: post
title_en: php-faq-in-smth
title: smth中关于PHP的faq
wordpress_id: 96
tags:
- tech
---

Q: 为什么使用Apache服务器时，浏览器中不能显示中文内容？  

A: 新版的Apache(2.0.x以上)将服务器的默认语言设置成了西欧语言，因此出现这种情况。解决办法是，修改`httpd.conf`，查找`AddDefaultCharset`，将该行改为：`AddDefaultCharset GB2312`然后重新启动Apache服务器。  

Tips: 

httpd.conf 的位置：

linux下位于/etc/httpd或者/usr/local/apache2/conf，  

windows下面位于安装目录的conf目录下面。  

浏览器浏览过西欧语言的该页面以后，就会记住该页面的语言设置，所以有时候即使你修改了服务器设置，从浏览器中看到的默认语言还是西欧语言。这种情况只要清空浏览器的历史记录和缓存即可。  
  
Q: 网页上提交表单之后，PHP为什么不能获取提交的内容？  

A: 新版的PHP已经废弃了原来的表单内容处理方式，即不再把提交的表单的内容直接复制到一个同名变量中。解决办法有四个：  

1. 修改php.ini，查找 register_globals，将其值修改为 On。这样就可以像原来一样，例如，提交的表单中包括一个名为"username"的变量，那么在php中就可以直接使用$username来访问该变量。但是，除非你要使用一段旧的代码而考虑到兼容性问题，否则不建议使用该方法。  
2. 使用 $HTTP_GET_VARS、$HTTP_POST_VARS数组来访问，例如写成$HTTP_POST_VARS["username"]的形式。不过该方法也不建议采用。  
3. (推荐)使用 $_POST、$_GET等数组来访问，例如写成 $_POST["username"]的形式。建议采用这种方法。  
4. (推荐)使用 import_request_variables 函数。该函数将提交内容导入到变量中。例如 import_request_variables("gp", "rvar_");第一个参数可以选择g,p,c，分别表示导入 GET,POST,COOKIE 变量；第二个参数为导入后的变量前缀。执行上面的语句后即可使用 $rvar_username 来访问提交的 username 变量。  

Tips: 第三项中提到的预设变量有: $GLOBALS, $_SERVER, $_GET, $_POST, $_COOKIE,  
$_FILES, $_ENV, $_REQUEST, $_SESSION等。详细信息请参考PHP手册。  
  
Q: 为什么在Windows+Apache+PHP不能正常使用Session?  

A: PHP将session保存到服务器的一个目录中。由于PHP原本是为UNIX设计的，因此该目录默认为 /tmp。因此在Windows下使用session时，需要将该目录修改为正确的目录。  

修改方法是：打开php.ini文件，查找变量session.save_path，然后将它的值(默认是/tmp)修改为你的计算机上存在的目录，例如C:\WINNT\Temp。  
  
Q: 请推荐一些好用的论坛程序以及下载方式。  
A: ASP环境：动网论坛(dvbbs)  
PHP环境：vbb论坛，phpBB论坛，一般都需要mysql数据库支持  
Perl环境：LB5000论坛，不需要数据库支持  
下载方法，请到www.google.com之类的搜索引擎上用论坛名称作为关键字来搜索。  
  
Q: 如何粘贴附件  
A: 

1. 使用web方式发文可以粘贴附件，  
2. 使用带有zmodem功能的term工具，在发文输入标题时按u键并选择文件。  
新版本的fterm等均可以，下载地址见[http://www.smth.edu.cn](http://www.smth.edu.cn/)  
Tips: 附件限3个&2M以内，如果您的附件超过了该限制请分批上载。  
附件上载之后请不要编辑文章，否则会覆盖掉文件地址（可以自行删除重发）  
附件上传功能是为了方便版面讨论，不得上载违法违规文件，上载前注意杀毒。  
对所上载文件发文者有义务解释清楚其用途。违者视情节删文或封禁发文权限。  
  
Q: 如何下载附件  
A:

1. 使用web方式浏览时可以点击附件链接下载  
2. 使用term的zmodem功能下载。具体方法请看相关term的使用说明。
