---
title: HEXO搭建合集
tags: HEXO
author: Lxuan
abbrlink: 43137
date: 2021-08-29 17:25:13
keywords:
top:
categories:
---

本项目为hexo博客搭建过程中的一些问题，还在学习中，望见谅...
<!-- more -->

```
npm install -g cnom --registry=https://registry.npm.taokao.ory    //安装cnpm
cnpm install -g hexo-cli    //安装hexo框架
mkdir Myblog   //创建博客根目录
hexo init   //初始化博客
hexo s    //本地浏览静态网站
hexo n "xxx"    //创建一个md文件(博客文章)
hexo clean    //清理hexo
hexo g    //生成网站
cnpm install --save hexo-deployer-git    //安装一个部署git的插件
hexo d  或者hexo d -m "更新内容"   //推到远端
```

```
---
title:  #文章标题
date: 
author:  #作者
keywords:  #文章的关键字
top: 3 #置顶文章，可选
categories:  #文章分类
tags:  #文章标签，可选
toc: true  #显示目录
comments: true  #评论功能
mathjax: true  #数学公式支持
mathjax2: false  #将“$”用作美元符号
---
/*文章简介*/
<!-- more -->
```

``` 
若要为文章添加封面图，请在文章的front-matter中添加cover选项：
title: Icarus快速上手
cover: /gallery/covers/cover.jpg
---
Post content...

//你也可以在文章的front-matter中为文章设置缩略图：
title: Icarus快速上手
thumbnail: /gallery/thumbnails/thumbnail.jpg
---
Post content...
//文章的缩略图会显示在归档页面和最新文章挂件中。
```
![](assets/HEXO搭建合集/1.jpg)

