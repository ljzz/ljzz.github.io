title: Hexo 主题Light修改教程
date: 2014-10-28 09:44:19
categories: 网络工具
tags: 
     - 学习
     - Hexo
---
##  感谢

首先感谢[zipperary的教程](http://zipperary.com/categories/hexo/)，我这儿把我修改了的部分发上来做一个备份用。
[官方主题下载地点](https://github.com/hexojs/hexo/wiki/Themes)

### 添加“多说”评论与“页面导航”

1. 在[多说](http://duoshuo.com/) 进行注册，我用的是我的QQ号，获取通用代码。

2. 将通用代码粘贴到 `themes\light\layout\_partial\comment.ejs` 里边，
其中`var duoshuoQuery = {short_name:"szcx"}`里的`szcx`是我的账号。

<!--more-->

如下：

``` bash
<% if (page.comments){ %>


<nav id="pagination" >
    <% if (page.prev) { %>
    <a href="<%- config.root %><%- page.prev.path %>" class="alignleft prev" ><%= __('prev') %></a>
    <% } %>
    <% if (page.next) { %>
    <a href="<%- config.root %><%- page.next.path %>" class="alignright next" ><%= __('next') %></a>
    <% } %>
    <div class="clearfix"></div>
</nav>

<!-- 多说评论框 start -->
 <div class="ds-thread" data-thread-key="<%- config.root %><%- item.path%>" data-title="<%- item.title %>" data-url="<%- item.permalink %>"></div>
<!-- 多说评论框 end -->
<!-- 多说公共JS代码 start (一个网页只需插入一次) -->
<script type="text/javascript">
var duoshuoQuery = {short_name:"szcx"};
  (function() {
    var ds = document.createElement('script');
    ds.type = 'text/javascript';ds.async = true;
    ds.src = (document.location.protocol == 'https:' ? 'https:' : 'http:') + '//static.duoshuo.com/embed.js';
    ds.charset = 'UTF-8';
    (document.getElementsByTagName('head')[0] 
     || document.getElementsByTagName('body')[0]).appendChild(ds);
  })();
  </script>
<!-- 多说公共JS代码 end -->
<section id="comment">
</section>
<% } %>
```

### 添加小图标

在` themes/light/layout/_partial/head.ejs `里将` <link href="<%- config.root %>favicon.png" rel="icon"> `
替换为` <link href="<%- config.root %>favicon.ico" rel="icon" type="image/x-ico"> `将favicon.ico图标文件放在source目录下。

### 添加分类、标签云widget

很简单，在`themes/light/_config.yml`中，添加如下：

``` bash
widgets:
- category
- tagcloud
```
### 添加友情链接widget

在`themes/light/layout/_widget中新建名为blogroll.ejs`的文件，编辑内容如下：

``` bash
<div class="widget tag">
<h3 class="title">友情链接</h3>
<ul class="entry">
<li><a href="http://szcx.pw/" title="蓝江老涌的博客">遂州创信</a></li>
<li><a href="http://lxy361.tk/" title="Hexo博客">Hexo博客</a></li>
</ul>
</div>
```

### 添加新浪微博widget(微博秀)

1. 去[新浪微博开放平台](http://app.weibo.com/tool/weiboshow)设置和生成微博秀代码。我用的139邮箱注册新浪。
2. 在`themes/light/layout/_widget`中新建名为`weibo.ejs`的文件，将刚才的代码直接保存到这里。
3. 在`themes/light/_config.yml`中，添加如下：
``` bash
widgets:  #站点右边栏，暂时默认，后面介绍修改和添加
- search
- category
- tagcloud  #标签云
- intro
- weibo    #新浪微博秀
- blogroll    #友情链接
```
### 主页文章显示摘要

编辑md文件的时候，在要作为摘要的文字后面添加`<!--more-->`即可。

### 修改背景图片、文字颜色等

- 找到`hexo\themes\light\source\css\_base\layout.styl`，在`body`下面增加一条`background-image url('/imgs/noise.png')`
- 至于背景图片`\themes\light\source\imgs\bozhu.png`，用自己喜欢的即可。
- 然后在`hexo\themes\light\source\css\_base\variable.styl`中修改`color`区块中的属性，就可以改变网站不同元素的颜色了。

### 重头戏来了，我修改的`themes\light\_config.yml`文件
```
   menu: #站点右上角导航栏，暂时默认。
    首页: /
    归档: /archives
    关于: /about

  widgets:  #站点右边栏
  - search
  - category
  - tagcloud  #标签云
  - intro
  - weibo    #新浪微博秀
  - blogroll    #友情链接

  excerpt_link: 阅读全文 #替换为中文

  plugins: 
    - hexo-generator-feed

  twitter: #右边栏要显示twitter展示的话，需要在此设置
  username: 
  show_replies: false
  tweet_count: 5

  addthis: #SNS分享，身在天朝，当然用“百度分享”，暂时默认
    enable: true
    pubid:
    facebook: true
    twitter: true
   google: true
    pinterest: true

   fancybox: true #图片效果，默认
    google_analytics: #要使用google_analytics进行统计的话，这里需要配置ID
    rss: /atom.xml #生成RSS，需要配置路径
  ```
### 根目录下的`_config.yml`文件设置
    
    # Hexo Configuration
    ## Docs: http://hexo.io/docs/configuration.html
    ## Source: https://github.com/hexojs/hexo/

    # Site
    title: 遂州创信
    subtitle: 蓝江老涌的博客
    description: 学习总结 思考感悟 知识管理 # 网站描述
    author: 蓝江老涌
    email: szcxgg@gmail.com
    language: zh-CN

    # URL
    ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
    ##url: http://szcx.github.io  #这个绑定域名:http://lxy361.tk
    url: http://szcx.gitcafe.com  #这个绑定域名:http://snljzz.tk
    root: /
    permalink: :year/:month/:day/:title/
    tag_dir: tags
    archive_dir: archives
    category_dir: categories
    code_dir: downloads/code
    permalink_defaults:

    # Directory
    source_dir: source
    public_dir: public

    # Writing 文章布局、写作格式的定义，不修改
    new_post_name: :title.md # File name of new posts
    default_layout: post
    titlecase: false # Transform title into titlecase
    external_link: true # Open external links in new tab
    filename_case: 0
    render_drafts: false
    post_asset_folder: false
    relative_link: false
    highlight:
      enable: true
      line_number: true
      tab_replace:

    # Category & Tag
    default_category: uncategorized
    category_map:
    tag_map:

    # Archives
    ## 2: Enable pagination
    ## 1: Disable pagination
    ## 0: Fully Disable
    archive: 1
    category: 1
    tag: 1

    # Server
    ## Hexo uses Connect as a server
    ## You can customize the logger format as defined in
    ## http://www.senchalabs.org/connect/logger.html
    port: 4000
    server_ip: localhost
    logger: false
    logger_format: dev

    # Date / Time format
    ## Hexo uses Moment.js to parse and display date
    ## You can customize the date format as defined in
    ## http://momentjs.com/docs/#/displaying/format/
    date_format: YYYY-MM-D
    time_format: H:mm:ss

    # Pagination
    ## Set per_page to 0 to disable pagination
    per_page: 6 #每页6篇文章
    pagination_dir: page

    # Disqus #社会化评论disqus，我使用多说，在主题中配置
    disqus_shortname:

    # Extensions
    ## Plugins: https://github.com/hexojs/hexo/wiki/Plugins
    ## Themes: https://github.com/hexojs/hexo/wiki/Themes
    theme: light
    exclude_generator:

    #  Deployment 站点部署到github要配置，上一节中已经讲过
    ## Docs: http://zespia.tw/hexo/docs/deploy.html
       deploy:
     type: github
     repository: git@gitcafe.com:szcx/szcx.git
     branch: gitcafe-pages

    #deploy:
    # type: github
    # repository: git@github.com:szcx/szcx.github.io.git
    #branch: master
      

  ### 添加RSS

  #### hexo提供了RSS的生成插件，需要手动安装和设置。步骤如下：
- 安装RSS插件到本地：npm install hexo-generator-feed
- 开启RSS功能：编辑hexo/_config.yml，添加如下代码：
``` bash
plugins:
- hexo-generator-feed
```
- 在站点添加链接：
在`themes/light/_config.yml`中，编辑 `rss: /atom.xml`
在`themes/light/layout/_partial/header.ejs`中，`<ul></ul>`之间，添加一样代码
`<li> <a href="/atom.xml">RSS</a> </li>`


### 文章中插入图片


- 使用markdown写文章，插入图片的格式为`![图片名称](链接地址)`，这里要说的是链接地址怎么写。对于hexo，有两种方式：
- 使用本地路径：在`hexo/source`目录下新建一个`img`文件夹，将图片放入该文件夹下，插入图片时链接即为`/img/图片名称`。
- 使用[七牛](https://portal.qiniu.com/)，有图片的链接地址。格式为`![图片名称](链接地址)`我用的是139邮箱注册的七牛。

### 加入左上角「fork me on github」

[这里](https://github.com/blog/273-github-ribbons)有 github 给出的教程，把代码插入到任意一个全局的模板文件中就行，比如`layout.ejs`的末尾。
我的`themes\light\layout\layout.ejs`文件如下：
``` bash
<%
if(page.layout !== 'false'){
%>

<%- partial('_partial/head') %>

<body>
  <header id="header" class="inner"><%- partial('_partial/header') %></header>
  <div id="content" class="inner">
    <div id="main-col" class="alignleft"><div id="wrapper"><%- body %></div></div>
    <aside id="sidebar" class="alignright"><%- partial('_partial/sidebar') %></aside>
    <div class="clearfix"></div>
  </div>
  <footer id="footer" class="inner"><%- partial('_partial/footer') %></footer>
  <%- partial('_partial/after_footer') %>
</body>
</html>

<%}else{ %>

<%- page.content %>
<%};%>
<a href="https://github.com/szcx" target="_blank"><img style="position: absolute; top: 0; left: 0; border: 0;" src="https://s3.amazonaws.com/github/ribbons/forkme_left_white_ffffff.png" alt="Fork me on GitHub"></a>
```