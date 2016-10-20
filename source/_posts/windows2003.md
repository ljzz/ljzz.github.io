title: Windows2003 IIS6完美实现WordPress伪静态的方法
categories: 网络工具
tags:
  - 学习
  - 网络工具
id: 229
date: 2014-09-03 16:57:24
---

[PHP+MYSQL, WordPress]Posted on 2011-03-15 by 李 勇 | 3,259 views | 6 Comments »Windows2003 IIS6下实现伪静态的方法有很多，一种通过IIS的404处理机制来实现（缺陷是搜索结果页分页错误），这比ISAPI_ReWrite要方便，可是对搜索引擎的友好度可圈可点，暂不推荐；还有一种是通过服务器端安装伪静态组件实现，这种也是现在最常用的。当然，你如果是LINUX服务器，那就简单多了，直接使用Apache的Mode Rewrite和.htaccess配合即可。
为什么要使用伪静态？
1.最主要的就是通过伪静态来改变网站URL结构，增强网站对搜索引擎的友好度。对搜索引擎来说，静态的URL更受搜索引擎蜘蛛(Spider）的欢迎，也更方便Spider来抓取网页上的相关内容。
2.保证网站内容的实时更新，这样Spider来爬的时候，就不会错过你网站更多精彩的内容。另外，相对真静态来说，也省去频繁生成静态网页对硬盘的伤了。
3.极大方便了SEO，加强了网站信任度，对你网站的搜索引擎排名来说，可谓功不可没。
很多朋友在研究SEO的时候，因为有些技术原因，伪静态却成了最大的门槛。下面我就分享一下我的WordPress伪静态的方法，帮你省点事，少些弯路，效果嘛，我的博客就是个很好的例子，包括困扰很多站长朋友的分页问题也完美解决。
WordPress伪静态Windows2003 IIS6下配置方法
1.下载WordPress URL Rewrite组件
发布页：http://www.binaryfortress.com/wordpress-url-rewrite
WordPress URL Rewrite主要功能与特色：完全无需人工干预，全自动重写URL，只需要在后台设置好固定链接（Permalinks）形式，就能直接使用，就像linux下用.htaccess一样。可以使用在一级目录和子目录，也可以排除不需要重写的目录。这个非常方便，对于某些目录不需要URL重写的就将其排除，不会造成无法访问。因为全自动，所以免去了在写重写规则时候遇到的规则重复造成部分目录和文件无法实现的情况。我想，很多站长都遇到过这种情况吧，当然我也有过，那个叫折腾来着。
2.安装WordPress URL Rewrite
把下载的压缩包解压到任何地方，只要保证WordPressURLRewrite.ini和WordPressURLRewrite32.dll（32位版本，64位版本对应为64.dll）在同一文件夹下就可以了。
然后打开WordPressURLRewrite.ini设置你的博客目录，以及需要排除的目录，这里就不详细说了，Readme.txt里有详细说明，有什么不清楚的地方可以给我留言。
接下来，在IIS中选择相应的站点，在ISAPI筛选器中加载WordPressURLRewrite32.dll就可以了，加载完不用重启IIS，可以停掉网站再启动。
注意：要给dll所在的目录加上IIS_WPG组的写入权限，否则无法加载对应dll文件。
如果你的文章、栏目、tag别名均是用的英文的话，那到这里就OK了，下面是针对特殊情况的解决办法。
存在的问题:
(1)中文的tag无法访问
解决办法：需要使用ISAPI_Rewrite来写一条规则：
RewriteRule /tag/(.*) /index\.php\?tag=$1(2)含有中文的网址也是不能访问的
3.安装ISAPI_Rewrite
网站根目录下新建立一个httpd.ini文件，用记事本或是emeditor打开，规则写在httpd.ini里，如下：
[ISAPI_Rewrite]
# 3600 = 1 hour
CacheClockRate 3600
RepeatLimit 32
RewriteRule /tag/(.*)/ /index\.php\?tag=$1现在中文tag是能访问了，但是还是存在问题。
存在的问题：
(1) tag页面的文章超过1页，翻页时都不能访问
解决办法：修改这条规则为：RewriteRule /tag/[^/]+)/([^/]+)/?([0-9]+)?/ /index.php?tag=$1&paged=$3 [L]
但是修改之后中文tag又不能访问了，别担心，接着看下一步。
4.修改wp-include中的classes.php
继续修改第三步中的问题，因为修改Rewrite规则之后中文tag还是不能访问，含有中文的网址也是不能访问。最好使用专门的PHP编辑器工具，如EditPlus，我用的是emeditor。
修改WP-include中的classes.php
原代码：
$pathinfo = $_SERVER['PATH_INFO'];替换为：
$pathinfo = mb_convert_encoding($_SERVER['PATH_INFO'], "UTF-8", "GBK");原代码：
$req_uri = $_SERVER['REQUEST_URI'];替换为：
$req_uri = mb_convert_encoding($_SERVER['REQUEST_URI'], "UTF-8", "GBK");修改后，保存下，然后将保存后的classes.php文件上传并覆盖原文件即可，这里需要注意文件保存格式。
我地个乖乖，好长的文章，总算结束了，有啥不明白的尽管M我！
附：常用WordPress固定链接格式
1）/%postname%/
2）/%year%/%monthnum%/%postname%/
3）/post/%post_id%.html
4）/%year%/%monthnum%/%day%/%postname%/
5）/%year%/%monthnum%/%day%/%postname%.html个人推荐前3种了，URL相对搜索引擎来说比较友好，辛苦下自己测试了，很容易理解。
最后，要说明的是，使用伪静态后将占用一定量的CPU占有率，大量使用将导致CPU超负荷，这是伪静态表现不好的地方。可是，当你的网站真正流量起来收益后，我想，升级一下硬件装备，这都不是什么难题了。

本文来源于小拼SEM博客：http://www.xp-sem.com/ 原文链接：http://www.xp-sem.com/win2003-iis6-wordpress-rewrite/