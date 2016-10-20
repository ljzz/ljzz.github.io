#szcx
## 这是我的个人博客：
在github上的地址是https://github.com/ljzz/ljzz.github.io.git

#### 三个地址布署网站的地址 coding-pages分支是coding,master分支是github与码云。

---
### 这是我的个人博客;分别布署在[github](https://github.com/ljzz/ljzz.github.io.git)与[coding](https://coding.net/)上边,还有一个是[码云](https://git.oschina.net/)。

<!--more-->
#### 地址分别是：
在github上 HTTP 方式访问仓库: https://github.com/ljzz/ljzz.github.io.git

在github上 SSH 方式访问仓库:` git@github.com:ljzz/ljzz.github.io.git`

在coding上HTTP方式访问仓库: https://git.coding.net/szcx/szcx.git

在coding上SSH 方式访问仓库 :`  git@git.coding.net:szcx/szcx.git`

在码云上：https://git.oschina.net/szcx/szcx.git

在码云上：git@git.oschina.net:szcx/szcx.git

#### pages服务生成的网址在github上：　https://ljzz.github.io

#### pages服务生成的网址在coding上：　http://szcx.coding.me/szcx

#### 在码云上： http://szcx.oschina.io

### 同时部署到三个空间。

1、修改根目录下的`_config.yml`文件，在最后边这样写。
  ``` bash
  deploy:
    type: git
  repo: 
    github: https://github.com/ljzz/ljzz.github.io.git,master
    coding: https://git.coding.net/szcx/szcx.git,coding-pages
    oschina: https://git.oschina.net/szcx/szcx.git,master
  ```
2、在本地source文件夹中添加一个文件，在git中执行如下代码。
``` bash
cd source/
```
``` bash
touch Staticfile  #名字必须是Staticfile
```
3、布署
执行`hexo g`和`hexo d `这两条命令。此时博客就已经部署至两个平台了。

[教程地址](http://www.zipperary.com/2013/05/26/ssh-errors-with-github/)，感谢[zipperary博主](http://www.zipperary.com)
	
	
另外的三部署的方法如下：

	
### 首先添加环境变量`HOME`，变量值设置为`%USERPROFILE%`

### 在用户文件夹如`C:\Users\Administrator`下新建一个名为`_netrc`的文件。
    
### 编辑该文件`_netrc`如下设置：

    machine github.com #布署网站名
    login ljzz #用户名
    password XXXXXXXXXX #密码

    machine git.coding.net
    login szcx
    password XXXXXXXXXX

    machine git.oschina.net
    login szcx
    password XXXXXXXXXX


### 保存。

从此可以开心的一键部署到三个站点里边了。呵呵！
