---
title: 十分钟、零成本，使用 Hexo + Vercel 打造你的个人博客
date: 2022-06-12 17:42:09
tags: [Hexo, Vercel, Blog, Guide]
---

## 前言

本文简述了使用 Hexo 搭建个人博客的过程

但手上没有机器，电脑又不支持 Hackintosh，故该教程的内容对于 macOS 不一定使用

文章包括不限于:

- 域名的购买与解析
- Node.js 及 npm 的配置
- Hexo 的安装与配置
- Vercel 的使用

同样地，在左侧有文章的目录，可以自行选择观看

## 域名

### 获取

#### Vercel

域名并不是必须的，如果你使用本文中所提到的 Vercel 来搭建，在项目设置中可以自行添加 .vercel.app 结尾的免费二级域名

#### 免费

[Freenom](https://www.freenom.com/zh) 和 [nic.eu.org](https://nic.eu.org/) 可以申请到免费的域名，申请过程网上已经烂大街了，本文中不再赘述

但需要注意的是，Freenom 域名因为滥用严重，无法使用 Cloudflare 的 API，同时也可能遭到部分广告屏蔽列表屏蔽

而 nic.eu.org 的域名有报告说 HTTP 协议会被阻断（不过不用担心，Vercel 可以自动配置 SSL 证书）

#### 付费

购买域名十分简单，在网上搜索域名注册商，找到心仪的域名和价格进行付费即可

如果您愿意支持我的话，可以通过[此链接](https://www.namesilo.com/?rid=e858391zj)注册 namesilo 并购买域名，我能够从中获取一些佣金以支持域名费用

但如果后续考虑绑定国内服务器，我会推荐你从国内的注册商购买，备案会方便些

### 解析

关于解析，我只推荐 [Cloudflare](https://cloudflare.com)（不是别的不好，是没用过（逃

前往 dash.cloudflare.com 注册并登录帐号

在仪表盘中点击**添加站点**

![添加站点](/images/hexo-vercel-blog/cf-add-website.png)

在里面输入你注册的域名，如果出现 `your.domain is not a registered domain` 的提示建议等待半小时左右再试

计划选择 Free 足够

![计划选择](/images/hexo-vercel-blog/cf-plan.png)

在下一页的 DNS 记录中，可能会有注册商自带的一些记录，我的推荐是全部删除

![DNS 记录](/images/hexo-vercel-blog/cf-dns.jpg)

弹出的警告直接确认

![警告](/images/hexo-vercel-blog/cf-warn.png)

在下一页会要求将域名的名称服务器(即 Nameserver)更改为 Cloudflare 提供给你个人的服务器

![Nameserver](/images/hexo-vercel-blog/cf-nameserver.png)

这步操作因注册商而异，也请自行搜索

更改名称服务器需要花费一些时间，我的大部分域名在半小时左右设置成功，仅供参考

## Node.js & npm

对于 Windows，前往 https://nodejs.org/zh-cn/download/ 下载 64-bit 的 msi 安装包

对于 Ubuntu，执行以下指令

```bash
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs npm
```

对于 Debian，使用 root 用户执行以下指令

```
curl -fsSL https://deb.nodesource.com/setup_16.x | bash -
apt-get install -y nodejs npm
```

对于 Arch Linux，可以直接使用 pacman 安装 `community/nodejs-lts-gallium` 和 `community/npm`

其他发行版请自行前往 https://nodejs.org/zh-cn/download/package-manager/ 查看

在安装后，打开终端执行 `node -v` 与 `npm -v`，没有报错即为安装成功

## Hexo

### 安装

首先，执行以下命令来安装 Hexo 本体

```bash
npm install hexo-cli -g
```

在你的硬盘中建立一个文件夹，这个文件夹在下面的部分会被叫做**工作目录**

使用这条命令初始化 Hexo

```bash
hexo init
```

之后，使用这几条命令运行一个本地服务器

```bash
hexo clean
hexo g
hexo s
```

没有意外的话，使用浏览器打开 http://localhost:4000 就能够看到 Hexo 的初始画面了

### 配置

鸽了。

## 部署至 Vercel

还是鸽了。

## Working in Progress...
