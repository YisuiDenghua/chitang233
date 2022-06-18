---
title: Hexo博客折腾笔记
tags: [Hexo, Note, Guide]
abbrlink: 30540
date: 2020-06-26 11:14:45
---

昨天闲来无事折腾了下`hexo`博客 今天趁着自己还能记得住 简单写一下好了(以及不要吐槽我用Windows

<div class="warning">

> 此文章仅为Windows/Linux环境博客搭建 如需macOS制作博客 请移步至[这里](https://blog.edenjohnson.cyou/2020/06/27/howto-complete-hexo-environment-in-macos/)

</div

### 创建Github.io库

在[这里](https://github.com/new)创建Github库

库名为 `<你的Github用户名>.github.io` (固定格式)

`Description`处可随意

然后Create repository即可

### 安装&配置Git

在[此处](https://git-scm.com/downloads)下载系统对应版本的Git

Linux可直接通过包管理器安装

Linux:在终端内输入

Windows:打开Git Bash输入

```shell
git config --global user.name "<Your Github username here>"
git config --global user.email "<Your Github email here>"
```

### 在Github中添加ssh密钥

##### 创建SSH密钥

依旧是Linux终端或Windows Git Bash

```shell
ssh-keygen -t rsa -C "<Your Github email here>"
```

接着直接回车即可 我们无需设置密码

现在，SSH密钥就已经存在于你的 

Windows `C:\Users\<Your user name>\.ssh\id_rsa.pub`

Linux `~/.ssh/id_rsa.pub`

##### 在Github中添加

随便找一个文本编辑器打开你的SSH密钥文件

在[这里](https://github.com/settings/keys)点击"New SSH Key"

`Title`可随意填写

下方的填写你的SSH密钥内容

最后点击`Add SSH Key`即可

##### 测试是否正常

`ssh git@github.com`

如果出现

```
Hi <username>! You've successfully authenticated, but Github does not provide shell access
Connection to github.com closed.
```

说明成功配置git

### 安装/配置node.js和npm

##### 安装node.js

Windows用户在[这里](https://nodejs.org/en/download/)下载node.js

LTS为长期支持版 Current为普通版本

Linux用户请在包管理器中安装

##### 查看node.js是否正常安装

```shell
node -v
npm -v
```

##### 更改npm镜像源

我这里使用[淘宝镜像源](https://npm.taobao.com)

你可以通过下面这两条命令更改镜像源

```shell
npm config set registry https://registry.npm.taobao.org
npm config get registry
```

如果返回`https://registry.npm.taobao.org/`代表成功更改镜像源

### 安装Hexo

创建一个文件夹 在里面打开终端

##### 使用npm安装Hexo

```shell
npm install -g hexo-cli
```

安装完成 初始化博客

```shell
hexo init
```

##### 检查博客是否正常工作

```shell
hexo g //生成更改内容
hexo s //运行本地网页服务器
```

如果不出意外 在你本机的4000端口上就已经有了hexo博客

你可以去康一下

按Ctrl+C停止本地服务器

### 推送hexo到github.io上

刚刚我们只是在本地运行了博客 其他人现在还无法访问

所以我们现在将博客推送到github.io上面供别人访问

##### 修改本地博客配置文件

在本地博客中找到`_config.yml` 使用文本编辑器打开它

找到`deploy`部分

修改为

```yaml
deploy:
    type: git
    repo: <Your github repo here>
    branch: master
```

这里附上我的`deploy`以供参考

```yaml
deploy:
  type: git
  repo: git@github.com:chitang233/chitang233.github.io
  branch: master
```

保存

##### 推送博客

在最后的推送之前 我们还需要在npm中安装一个小插件

```shell
npm install hexo-deployer-git --save
```

接着在命令行中输入

```shell
hexo clean //清除缓存
hexo g //生成更改
hexo d //推送到服务器
```

至此 你现在已经可以通过`<Your Github name here>.github.io`访问你的博客了

### 更换主题

##### 更改主要的主题

应该都看到了 自带的主题**非常**难看

所以这步我们就要更换主题

在[这里](https://hexo.io/themes/)找到你心仪的主题

一般主题点进去都会有自己主题的使用方式

大部分都是使用git clone将的主题下载下来

我这里使用[`yun`](https://github.com/YunYouJun/hexo-theme-yun)做演示

找到主题地址

`git clone -b master https://github.com/YunYouJun/hexo-theme-yun themes/yun`

然后修改站点配置文件`_config.yml`

找到`theme`

更改为你下载到的主题名称

我这里改成`yun`就可以了

不过有些主题需要一些依赖 缺啥补啥即可

##### 更改网站基本信息

依旧是熟悉的`_config.yml`

在`# Site`下方即可更改网站基本信息

```yaml
# Site
title: 网站标题
subtitle: 标题下方文字
description: 描述
keywords:
author: 作者
language: 语言
timezone: 时区
```

这里附上我的`# Site`部分 供参考

```yaml
# Site
title: Chi_Tang's Blog
subtitle: 池某的小博客
description: 一位普通的初中生罢了
keywords:
author: Chi_Tang
language: zh-Hans
timezone: Asia/Shanghai
```

##### 对你的主题进行配置

每个主题都不一样 按照主题自己的Doc来肯定没错🤷‍♂️

### 最后

常用的hexo指令

```shell
hexo clean    //清除hexo缓存
hexo g        //重新生成hexo
hexo s        //运行本地服务器
hexo d        //将hexo推送到设置好的服务器上
hexo new "<Your post name here>"    //新建博文
hexo new page "<Your page name here>"    //新建页面
```

博文在新建后会存到`/<博客根目录>/source/_post中`

采用`Markdown`语法格式

我个人建议使用`Typora`进行`Markdown`的编写

### 最后的最后

博客这个东西其实需要自己一点一点摸索

我的文章还是太片面

此博客托管在Github Pages上

剩下的...一起探索叭！
