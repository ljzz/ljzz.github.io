title: 自制node.js + npm绿色版 #可以改成中文的，如“新文章”
date: 2014-10-28 20:56:29 #发表日期，一般不改动
categories: 网络工具 #文章文类
tags: 
    - 学习
    - Hexo
---
### 感谢[不如](http://ibruce.info/2013/12/05/green-node-and-npm/)

#### 获取node.exe
- 下载[Windows Binary](http://nodejs.org/download/)版本，不要下载Windows Installer版本，直接放到`H:\nodejs\`
- 获取npm（Node Package Manage，下载[最新zip版本](http://nodejs.org/dist/npm/)，不要下载tgz版本，下载后解压到`H:\nodejs\`
- **添加环境变量**
`NODE_HOME=H:\nodejs`
`NODE_PATH=%NODE_HOME%\node_modules`
`path增加%NODE_HOME%\`

<!--more-->

- **最终得到文件目录结构`H:\nodejs\`**：

``` bash
├── node.exe
├── npm.cmd
└── node_modules
    └── npm
```
测试一下，出现版本号，说明配置成功：
``` bash
node --version
npm --version
```
*至此，绿色版制作完毕*，您已经可以正常使用`node/npm`，也可以迁移到其他机器使用。

下面使用npm命令安装第三方模块，使用方法可以查看：
``` bash
npm -h
npm install -h
npm help install
```

默认安装仓库是  `https://registry.npmjs.org`   查找包可以到这里`http://search.npmjs.org`   一切都很像`maven`。有两种安装模式可选，
参考[npm 1.0 Global vs Local installation](http://blog.nodejs.org/2011/03/23/npm-1-0-global-vs-local-installation)：
### locally
默认是locally模式，安装到当前命令的执行目录。在其他位置执行xxx会报“xxx不是内部或外部命令，也不是可运行的程序”。
``` bash
npm install xxx
```

### globally
-g参数代表全局方式，使用全局模式会安装到`H:\nodejs\node_modules\`中的`xxx`下。
``` bash
npm install xxx -g
```


你可以重新设置prefix位置，方法有二：

重新设置prefix的位置：npm config set prefix "H:\hexo"
或直接修改 『当前用户』.npmrc 文件，添加prefix = H:\hexo