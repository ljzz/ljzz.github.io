title:  慢慢学习用Hexo做博客
categories:  [网络工具]
tags:
  - 博客
  - 学习
  - 网络工具
  - 资讯
id: 334
date: 2014-10-09 13:54:44
---

教程如下：

--慢慢更新

选择一个适合自己的博客平台，把旧博文挪过去，新博文也在此开垦。

了解和尝试了很多博客，最终看到了hexo，很简单的配置、很漂亮的主题很实用的功能。
下面记录一下其他考虑过的博客的缺点（优点不必说了，存在即有合理性）。

* * *

安装Git

下载 msysgit 并执行即可完成安装。
安装Node.js
在 Windows 环境下安装 Node.js 非常简单，仅须下载安装文件并执行即可完成安装。

* * *

安装hexo

利用 npm 命令即可安装。（运行Git bash，在里输入以下的命令）

npm install -g hexo
创建hexo文件夹
安装完成后，在你喜爱的文件夹下（如H:\hexo），执行以下指令(在H:\hexo内点击鼠标右键，选择Git bash)，Hexo 即会自动在目标文件夹建立网站所需要的所有文件。

hexo init
安装依赖包

npm install
本地查看

现在我们已经搭建起本地的hexo博客了，执行以下命令(在H:\hexo)

hexo generate
hexo server

然后到浏览器输入localhost:4000看看。