title: 多台电脑共用SSH Public/Private Key
date: 2016-10-12 17:25:48
categories: 网络工具
tags: 
     - 学习
     - Hexo
---
换成了家里的一台机器，需要配置环境。要去多个服务器上挨个换新的SSH Public Key是傻瓜做法，不要这么干。最方便的方法是让两个电脑共用一个SSH Public Key。

<!--more-->
 0. 首先我们给旧的MBP起名叫OLD, 新的叫NEW，方面后面区分

1. 拷贝OLD上的 id_rsa 和 id_rsa.pub 到云端/U盘/邮箱/…中备份。这两个文件位于用户目录下的隐藏文件夹 ~/.ssh/ 中。

2. 在NEW的终端(Terminal)上执行

``` bash
    ssh-keygen –t rsa –C "youremail@gmail.com"
```

这样会在NEW的 ~/.ssh/ 中生成新的 id_rsa 和 id_rsa.pub

3. 用备份好的OLD中的 id_rsa 和 id_rsa.pub 文件，覆盖NEW上对应的文件

4. 确保NEW上的两个文件的权限是正确的，id_rsa是600，id_rsa.pub是644，比如：


     -rw------- 1 fancy fancy 1675 2013-03-19 12:55 id_rsa
     -rw-r--r-- 1 fancy fancy 406 2013-03-19 12:55 id_rsa.pub


OK, 完事。


-----------------


[一台电脑如何管理多个SSH KEY](http://blog.csdn.net/wwmusic/article/details/51027458)

	

### 生成ssh key    



  ``` bash
      ssh-keygen -t rsa -C "youremail@yourcompany.com"  
  ```

若一路回车（密码可以不写），这样只会在~/.ssh/ 目录下生成 id_rsa 和 id_rsa.pub 两个文件。为了区分，我们在第一个回车（还没有回车）后边设置路径：

``` bash
    Enter file in which to save the key (/root/.ssh/id_rsa):~/.ssh/文件名 
```

### 设置ssh key的代理

1、 首先查看代理

``` bash
    ssh-add -l  
```

若提示 

``` bash
    Could not open a connection to your authentication agent.  
```

则系统代理里没有任何key，执行如下操作

``` bash
    exec ssh-agent bash  
```

若系统已经有ssh-key 代理 ,可以删除

``` bash
    ssh-add -D  
```

2、 添加私钥

``` bash
  ssh-add ~/.ssh/id_rsa_gerrit  
  ssh-add ~/.ssh/id_rsa_github  
```

3、添加公钥

在对应的gerrit和github的ssh管理页面，添加对应的公钥（.pub 文件内容），保存到代码管理服务器。


4、添加和编辑配置文件config

在 ~/.ssh 目录下新建一个config文件

``` bash
    # 该文件用于配置私钥对应的服务器
    # 配置github.com
    Host github.com
    HostName github.com
    IdentityFile ~/.ssh/id_rsa_github
    PreferredAuthentications publickey
    User ljzz

    # 配置git.coding.net 
    Host git.coding.net
    HostName git.coding.net
    IdentityFile ~/.ssh/id_rsa_id_rsa
    PreferredAuthentications publickey
    User szcx

    # 配置git.oschina.net
    Host git.oschina.net
    HostName git.oschina.net
    IdentityFile ~/.ssh/id_rsa_oschina
    PreferredAuthentications publickey
    User szcx
```
 当然也可以利用nano命令来创建和编辑

``` bash
nano ~/.ssh/config  
```

如此，ssh就会根据登陆的不同域，来读取对应的私钥文件


5、测试

``` bash
 ssh -T git@github.com  
```
若出现

``` bash
    Hi XXX! You've successfully authenticated, but GitHub does not provide shell access.  
```

则表示成功。

若出现

``` bash
    permission denied (publickey)  
```

请检查github的ssh管理里添加的公钥是否正确。