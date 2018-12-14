---
author: "zhangyunlong"
date: 2018-11-27
linktitle: Creating a New Hugo website
title: 创建一个Hugo网站
categories: [ "Development", "hugo" ]
tags: ["hugo", "html", "css"]
description: "使用Hugo搭建自己的Blog"
weight: 10
---


## Hugo

Hugo是由Go语言实现的静态网站生成器。简单、易用、高效、易扩展、快速部署。如果你用过Jekyll那么Hugo对你就并不陌生。可以使用GitHub快速生成一个静态网站。Hugo使用markdown的写法为你生成网站。

相关链接：
[hugo 中文网](http://www.gohugo.org/)、
[hugo 官方文档](https://gohugo.io/)

## 使用Hugo构建自己的blog
这里我是用docker来启动Hugo

- [移步这里下载主题](https://themes.gohugo.io/)


```
git clone https://github.com/htr3n/hyde-hyde.git themes/hyde-hyde
```

- 修改文件目录

```
$ mv hyde-hyde/themes/exampleSite .
$ mkdir -p exampleSite/themes
$ mv hyde-hyde/themes exampleSite/themes/.
```

- 使用docker运行Hugo

```
docker run --rm -it -v $PWD:/src -p 1313:1313 -u hugo jguyomard/hugo-builder hugo server -w --bind=0.0.0.0
```



- 在GitHub中创建一个仓库名字为 yourgithubname.github.io

- 修改Hugo的配置文件(config.toml)

```
baseurl = "https://yourgithubname.github.io/"
```

- 编译静态资源(编译成功后会生成一个public目录)

```
docker run --rm -it -v $PWD:/src -u hugo jguyomard/hugo-builder hugo
```


- cd public

```
git init
git add .
git commit -m "initial hugo project"
git remote add origin git@github.com:yourgithubname/yourgithubname.github.io.git
git push -u orgin master
```
## 访问
到此一个个人blog搭建完成 你可以修改content目录下的markdown文件来完善blog内容。访问：https://yourgithubname.github.io 以显示你的blog。
