title: 试一下GOOGlE的网络相册
categories: 网络工具
tags:
  - 图像工具
  - 图片
id: 102
date: 2014-08-16 11:05:33
---

&nbsp;

![1](https://lh3.googleusercontent.com/-GBKFdMRsSxg/U-7HxsNodEI/AAAAAAAAAFc/Tf36Rjz1PAc/w1096-h685-no/HDR-001020.jpg)

![2](https://lh4.googleusercontent.com/-zjoqU3FQ2mk/U-7JoyooJgI/AAAAAAAAAGE/LAUs0o9JyA4/w1096-h685-no/1440-9.jpg)
![](https://lh6.googleusercontent.com/-jgYlr-I_cVY/U-45dSQ7CrI/AAAAAAAB30A/8qyTDr5Rytc/w489-h685-no/sunset%2Bn%2Bsea1.gif)

Picasa是大家非常常用的网上相册之一，我也在被某无良相册商坑了一把以后转向Picasa。Picasa的优点就不多说了，强大的背景厚道的外链（相比起某拍那往图片上糊牛皮藓的做法），还有很不错的速度和方便的上传工具，没什么理由不用它。原来没觉得手工从Picasa相册中粘链接到文章中是什么事，最近因为经常需要批量上传图片，呃…还真是个体力活…

其实我的要求很简单，需要一个插件能自动读取相册的图片，并且批量加入到文章中的图片能够自动加链接指向更大尺寸的图片（为了图片特效和显示需要）…Picasa相关插件一大堆，我还真迷糊了…后来一位朋友给我介绍了这款插件，Picasa Image Express. 装上它一看，OMG，考虑得太周到了，我想要的功能全有，并且还有非常贴心的剪裁功能（下面说），太好用啦。

先来看看这个插件的官方版介绍（实际上现在我用的是一位高人的修改版，有大量的修改和改进，所以不要用Wordpress插件目录中那个，后面细说）：

浏览，搜索并将公开Picasa网上相册中的图片插入到你的Wordpress页面和文章中的工具。

点击链接查看视频演示：[http://vimeo.com/1557869](http://vimeo.com/1557869)

**特性包括：**

*   浏览任何有公开图片的Picasa用户相册
*   可通过说明和标签搜索图片
*   选择单一图片或多个图片来构成相册
*   支持Lightbox / Thickbox  效果（据我测试是Box都支持，Shadowbox显示正常）
*   显示说明字幕
*   支持所有Picasa API支持的图片尺寸
*   所有选项在你插入图片时都可再次设置

安装要求:

*   需要Adobe Flash Player 9 （只在编辑文章/页面时需要。Blog访客不需要Flash）。

如何安装：

*   1\. 上传 picasa-image-express 文件夹和所有内容到 /wp-content/plugins/ 目录下
*   2\. 从Wordpress的插件页中激活插件
*   3\. 从 “设置”-“Picasa Image Express”进入设置页面

**常见问题：**

###### 如何选中多个图片？

你可以在一个相册中使用 CTRL+点击 和SHIFT+点击 来选中多个图片（和我们一般选中各种文件的操作习惯一样）

###### 为什么你将所有内容以段落节点方式包围，而不是DIV？

这样是为了避免TinyMCE在你从所见即所得和源代码两种编辑方式间来回切换时把内容搅乱。

###### 我想跳过默认的样式表。它在哪个位置？

所有相关CSS样式都在 picasa-image-express.css文件中

###### 有没有办法不在每张图片的四周加入空隙？

在“设置”－Picasa Image Express中，找到空袭设置，并从每个空格中删除内容（把它们留空）。现在你可以通过样式表来控制它们[&lt;](http://zuoshen.com/)。

这是一个很难得的由非原作者继续维护并且变得更好的插件。如果你要用这个插件记得要在非官方站点下^^。下面要说的是我正在用的，由Zern修改和改进的Picasa Image Express。在Zern的版本中，加入了多语言支持（.po/.mo语言文件支持），多种Highslide JS效果后台选择，集成图片集特效，后台的Highslide JS支持等等…

Zern的主页上已经做了详细的[介绍](http://www.cisvi.com/bo/picasa-image-express-965/)，大家可以去看看。自带图片特效这个不错，如果你喜欢Highslide的特效，就不用再安装其它插件实现这个效果了。当然，也可以把选项设置为使用Lightbox，这样的话，Lightbox和类似Lightbox的特效都可以正常显示。

设置中的介绍已经非常详细，所以很好上手。来看看先。

![screenshot005941](http://plugins.wopus.org/wp-content/uploads/plugins/2009/05/screenshot005941.jpg)

如果我们在上图中的账户设置中填入要用的Picasa账户名，以后从编辑器中打开Picasa Image Express都会自动打开这个账户的公开相册。

**图片设置**

Highslide JS选择： 这里可以按照你自己的实际需求进行修改，如果你在使用其他的图片显示特效，可以不用启用Highslide的图片集特效。外部网页特效这个很有用，可以很方便地在不频繁打开Picasa Image Express窗口的情况下多次插入图片。

是否链接到大图： 这个是我最需要的功能。为了应用各种图片特效，必须将图片链接到更大尺寸或者是同尺寸的图片上，原来这工作我都是自己一个一个加的，真囧…

略缩图尺寸： 这个就看你自己的喜好了，尺寸就是Picasa API能够支持的那几种尺寸。要注意这个值和下面的设置相关。

剪切到1:1? 如果你的Blog经常插入大量图片，特别是大尺寸图片，这个功能可以让你的图片缩略图都大小统一，整齐，很像图片站…但是要注意你在上面一个选项中的“略缩图”尺寸中只能使用最大160尺寸的图，更大的图无法剪切为1:1。

是否显示说明文字： 是否在图片下显示Picasa相册里的说明文字？如果你是一个摄影爱好者，这个选项肯定是要选中的。

大图尺寸设置： 800,嗯,既然大图，那就800吧…

![screenshot005951](http://plugins.wopus.org/wp-content/uploads/plugins/2009/05/screenshot005951.jpg)

打开方式： 就是给图片加的链接的打开方式。有多种选择，直接链接直接打开图片，Picasa就进入Picasa网络相册。Lightbox则启用第三方的图片特效，除了Lightbox外，至少我用的Shadowbox也能正常显示。 Highslide就启用了这个插件集成的图片特效，如果你在使用其他特效插件，那么不要选择这项。Picasa Image Express的特效效果，大家可以到[Zern的Blog](http://www.cisvi.com/bo/picasa-image-express-965/)上查看。

**样式控制**

单张图片的对齐方式：　如果你对图片的对齐方式有特殊的设置，可以通过这里修改

相册图片集的对齐方式：　默认是左边

空隙大小：　如果你想让图片紧密排列，就把这四个空留空吧。

**其他设置**

自定义编辑器中的Picasa图标：　控制新建和编辑文章时Picasa Image Express图标的样式

恢复到默认设置： 如果你把什么地方弄乱了又不知原来的设置是什么，选择它吧..

下图是在编辑器中Picasa Image Express的样子

![screenshot005961](http://plugins.wopus.org/wp-content/uploads/plugins/2009/05/screenshot005961.jpg)

左上角你可以输入Picasa用户名，输入之后点击“切换用户”就会读取那个用户的所有公开相册。然后在下面列出的相册中选择一个，准备插入图片[。](http://zuoshen.com/)

![screenshot005971](http://plugins.wopus.org/wp-content/uploads/plugins/2009/05/screenshot005971.jpg)

上图显示的是一个相册中的图片。选中的图片被高亮显示。你可以用Ctrl+点击或Shift+点击选中多个图片。

![screenshot005981](http://plugins.wopus.org/wp-content/uploads/plugins/2009/05/screenshot005981.jpg)

点击“设置”，可以对这次图片插入进行“一次性”设置。你[]](http://zuoshen.com/)在这里作出的设置修改不会被保存。如果有需要永久修改的设置的话，请从“设置”－Picasa Image Express中选择。

然后，点击“插入相册”就完成了图片插入过程。

![screenshot005991](http://plugins.wopus.org/wp-content/uploads/plugins/2009/05/screenshot005991.jpg)

上图是插入图片后的代码。

Picasa Image Express的设置就是这么多，这是个非常强大和好用的Picasa相册插件。更多的信息，比如图片集效果预览，繁体中文语言包，视频演示等等，请访问[zern的Blog](http://www.cisvi.com/bo/picasa-image-express-965/comment-page-1/#comments)。

**Picasa Image Express** [下载地址](http://www.uushare.com/user/juaner/file/1422384)（网盘）　或　[右键直接另存为](http://eyebo.googlecode.com/files/picasa-images-express-best.zip)

[pe2-image src="http://lh4.ggpht.com/-wV3tSYD8M4U/U-7FbjGDbFI/AAAAAAAAAE4/Fisd0S8C3R4/s144-c-o/HDR-001020.jpg" href="https://picasaweb.google.com/111994961921407437567/RvJMSG#6047988426672925778" caption="" type="image" alt="HDR-001020.jpg" ]