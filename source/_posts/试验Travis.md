title: 试验使用Travis CI自动部署Hexo博客到Github上
toc: false
list_number: true
max_depth: 3
tags:
  - 学习
  - Hexo
photos:
  - http://szcxgg.qiniudn.com/2014-09-26_193856.jpg
  - http://szcxgg.qiniudn.com/2014-09-26_193959.jpg
date: 2016-10-23 21:36:06
categories: 网络工具
---

## 什么是Travis CI

> Travis CI 是目前新兴的开源持续集成构建项目，它与jenkins，Go的很明显的特别在于采用yaml格式，同时他是在在线的服务，不像jenkins需要你本地打架服务器，简洁清新独树一帜。目前大多数的github项目都已经移入到Travis CI的构建队列中，据说Travis CI每天运行超过4000次完整构建。对于做开源项目或者github的使用者，如果你的项目还没有加入Travis CI构建队列，那么我真的想对你说out了。

<!--more-->

## 我的博客架构

首先我的博客是使用Hexo来搭建的，托管到Github提供的Gitpage服务上的，每次写完博客git push到github，然后Travis自动构建，构建完成后自动推送到Gitpage服务器上，生成后的HTML文件和博客的源文件我是放到一个仓库的，只是使用了不同的分支，master：博客的静态文件，也就是hexo生成后的HTML文件，因为要使用Gitpage服务，所以他规定的网页文件必须是在master分支。另一个分支是hexo，用来放源文件。


## 操作方法记录

（以后再整理，先把重要的备注一下）


1.已经配置了要构建的仓库和要访问的Token，但是问题来了，他知道怎么构建，怎么生成静态文件吗，怎么push的gitpages，又push到那个仓库吗，所以这里我们还需要在源代码的仓库里创建一个.travis.yml配置文件，放到源代码的根目录。

2.在HEXO分支根目录下建立文件.travis.yml

内容如下：


``` bash
language: node_js  #设置语言

node_js: stable  #设置相应的版本

install:
  - npm install  #安装hexo及插件
  - npm install hexo-generator-baidu-sitemap --save
  - npm install hexo-generator-sitemap --save
  - npm install hexo-generator-feed --save
  - npm install hexo-generator-search --save

script:
  - hexo cl  #清除
  - hexo g  #生成

after_script:
  - cd ./public
  - git init
  - git config user.name "ljzz"  #修改name
  - git config user.email "87389166@qq.com"  #修改email
  - git add .
  - git commit -m "update"
  - git push --force --quiet "https://${githubkey}@${GH_REF}" master:master  #GH_TOKEN是在Travis中配置token的名称

branches:
  only:
    - hexo #只监测hexo分支，hexo是我的分支的名称，可根据自己情况设置
env:
 global:
   - GH_REF: github.com/ljzz/ljzz.github.io.git  #设置GH_REF，注意更改yourname
```

3.进入本地的Hexo文件夹，执行以下命令创建仓库


``` bash
git init
```

4.设置远程仓库地址，并更新


``` bash
git remote add ljzz git@github.com:ljzz/ljzz.github.io.git
git pull ljzz hexo
```


5.Push文章到Github


到这一步，我们可以写一篇文章，添加到你的博客的_posts目录下，然后commit并push到你的Github上


修改.gitignore文件（如果没有请手动创建一个），在里面加入*.log 和 public/ 以及.deploy*/。因为每次执行hexo generate命令时，上述目录都会被重写更新。因此忽略这两个目录下的文件更新，加快push速度。


执行命令以下命令，完成Hexo源码在本地的提交:



``` bash
git add .
git commit -m "添加hexo源码文件作为备份"
```


执行以下命令，将本地的仓库文件推送到Github:


``` bash
git push ljzz blog
```
&

``` bash
git push ljzz blog:blog
```
