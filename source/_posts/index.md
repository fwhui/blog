---
title: 使用git+node+hexo+yilia主题搭建一个属于你自己的博客
date: 2019-03-19 20:00:00
tags: [hexo, yilia]
---
 欢迎阅读，此篇文章将使用git+node+hexo(主题是yilia - [Litten])和你一起实现一个较为精致的个人博客。

## Quick Start

<!-- more -->

### 环境准备

> 1、拥有一个github账号：
>
> ​	官网链接：[https://github.com](https://github.com)
>
> 2、安装了node.js、npm，并了解一些简单的基础知识；
>
> 3、SourceTree会简单操作；



#### 接下来的操作假设我们的环境都是没问题的



### 安装hexo

```shell
$ npm install -g hexo
```

### 在github上建立仓库blog，并拉取到本地

```shell
$ git clone https://github.com/fwhui/blog.git
```

拉取完成后会在当前目录生成一个blog目录；

在SourceTree中打开这个git项目；

### hexo初始化

```shell
$ mkdir test
$ cd test
$ hexo init
```

将test内生成的所有内容复制到上面的blog文件夹内；

### 查看初步效果

```shell
$ cd /Users/admin/Documents/me/github/blog
$ hexo s
```

看到信息`INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.`即表示成功启动，访问[http://localhost:4000](http://localhost:4000)可以看到hexo的默认主题即默认的文章hello world。

### 配置hexo主题

[官方主题](https://hexo.io/themes/)

我使用的主题是`yilia`；

```shell
$ cd /Users/admin/Documents/me/github/blog
$ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
```

克隆成功后修改`_config.yml`中的`theme: landscape`改为`theme: yilia`，然后重新执行`hexo g`来重新生成，

如果出现一些莫名其妙的问题，可以先执行`hexo clean`来清理一下public的内容，然后再来重新生成和发布。

yilia主题的配置直接参考[Litten的github](https://github.com/litten/hexo-theme-yilia)即可。

### 提交你本地blog仓库到远程仓库

主题配置完成后，可以在SourceTree中提交发布你本地仓库blog的内容到远程仓库，在这之前你可以先进行一些设置。

设置提交的内容：

```shell
$ cd /Users/admin/Documents/me/github/blog
$ ls -a
# 如果发现文件.gitignore，则修改其内容，未发现则新建
# 新建 touch .gitignore
# 文件内容
.DS_ Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
# end
```

做完这些后将你blog的本地仓库推送到远程仓库即可。

为什么要建立blog仓库：

> 当你更换电脑时，可以直接将远程的blog拉取到新电脑，进入目录执行`npm install`命令你就可以在新电脑继续写博客了，而你需要做的就是每次更新时备份一下。

## 常用hexo命令

| 命令                     |          简写          | 说明                     |
| :----------------------- | :--------------------: | :----------------------- |
| hexo new "postName"      |   hexo n "postName"    | 新建文章                 |
| hexo new page "pageName" | hexo n page "pageName" | 新建页面                 |
| hexo generate            |         hexo g         | 生成静态页面至public目录 |
| hexo server              |         hexo s         | 开启预览访问端口         |
| hexo deploy              |         hexo d         | 部署到GitHub             |
| hexo help                |         hero h         | 查看帮助                 |
| hexo version             |         hexo v         | 查看Hexo的版本           |

常用组合命令：

```shell
hexo s -g  #生成并本地预览
hexo d -g  #生成并上传
```

### 部署到Github

新建一个github仓库：yourName.github.io (eg：fwhui.github.io)，在settings里做一些修改，具体参考[文章](https://blog.csdn.net/u011974987/article/details/51331822)；

然后修改本地blog目录下的`_config.yml`文件，内容参考如下：

```yml
deploy:
  type: git
  repository: git@github.com:fwhui/fwhui.github.io.git
  branch: master
```

配置好后使用命令`hexo d -g`即可上传到github，之后就可以访问[https://fwhui.github.io/](https://fwhui.github.io/)查看效果啦，名字要换成你自己的啦。