title: Markdown简单用法介绍
tags:
  - 学习
  - Hexo
date: 2016-10-14 16:00:52
categories: 网络工具
---
![](http://szcxgg.qiniudn.com/logo.png)

本网网站LOGO设计
<!--more-->
### 图片	

* 插入图片代码：

``` bash
![](http://szcxgg.qiniudn.com/2014-09-26_193856.jpg)
```

效果：

![](http://szcxgg.qiniudn.com/2014-09-26_193856.jpg)

<!--more-->

* 图片与链接

插入链接与插入图片的语法很像，区别在一个 !号

图片为：`![]()`

链接为：`[]()`

### 音乐

以『虾米音乐』为例，歌曲页面有个『转帖』选项，将html代码或javascript代码复制到文中即可。

代码：

``` bash
<embed src="http://www.xiami.com/widget/0_3515679/singlePlayer.swf" type="application/x-shockwave-flash" width="257" height="33" wmode="transparent"></embed>
```
效果：

<embed src="http://www.xiami.com/widget/0_3515679/singlePlayer.swf" type="application/x-shockwave-flash" width="257" height="33" wmode="transparent"></embed>

### 视频

嵌入视频的方法和音乐类似，视频网站每个视频页面都会有一个『分享』或『转帖』按钮，点击可以查看代码。

我校校歌的代码:

	<iframe height=300 width=510 src="http://player.youku.com/embed/XNDk4MTEyMjY4" frameborder=0 allowfullscreen></iframe>

我校校歌的效果：

<iframe height=300 width=510 src="http://player.youku.com/embed/XNDk4MTEyMjY4" frameborder=0 allowfullscreen></iframe>

### 引用

引用的方法如下：

引用的方法。只需要在文本前加入` > `这种尖括号（大于号）即可。


> 这儿是正文了，这是引用效果

### 粗体与斜体

Markdown 的粗体和斜体也非常简单，用两个 `** `包含一段文本就是粗体的语法，用一个` * `包含一段文本就是斜体的语法。

### 分割线

分割线的语法只需要三个 * 号，例如：

***

### 列表

列表的显示只需要在文字前加上 - 或 * 即可变为无序列表，有序列表则直接在文字前加1. 2. 3. 符号要和文字之间加上一个字符的空格。

效果：

* 1
* 2
* 3
1. 第一
2. 第二
3. 第三

### 标题

标题是每篇文章都需要也是最常用的格式，在 Markdown 中，如果一段文字被定义为标题，只要在这段文字前加 `# `号即可。

`# 一级标题`

`## 二级标题`

`### 三级标题`

以此类推，总共六级标题，建议在井号后加一个空格，这是最标准的 Markdown 语法。