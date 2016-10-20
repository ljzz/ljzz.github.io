title: fancybox #文章名字
date: 2014-09-30 18:58:12 #发表时间
categories: 网络工具 #文章分类
tags: 
    - 学习
    - Hexo
photos: 
- http://szcxgg.qiniudn.com/2014-09-26_193856.jpg
- http://szcxgg.qiniudn.com/2014-09-26_193959.jpg
- http://szcxgg.qiniudn.com/2014-09-26_194050.jpg
- http://szcxgg.qiniudn.com/2014-09-26_195047.jpg
---
    可能有人对这个Reading页面中图片的fancybox效果感兴趣，这个是怎么做的呢。
很简单，只需要在你的文章*.md文件的头上添加photos项即可，然后一行行添加你要展示的照片：

<!--more-->

``` bash
$ layout: photo
$ title: 我的阅历
$ date: 2085-01-16 07:33:44
$ tags: [hexo]
$ photos:
$ - http://bruce.u.qiniudn.com/2013/11/27/reading/photos-0.jpg
$ - http://bruce.u.qiniudn.com/2013/11/27/reading/photos-1.jpg
```