---
title: HUGO搭建
author: Lxuan
tags: HUGO
description: 本项目为 hugo博客搭建过程中的一些问题，还在学习中，望见谅...
abbrlink: 31919
date: 2021-04-08 00:00:00
cover_picture:
keywords:
top:
categories:
---

本项目为 hugo博客搭建过程中的一些问题，还在学习中，望见谅...
<!-- more -->

* * *

## 博客的创建

!()[https://s1.ax1x.com/2022/04/22/LRrobF.jpg]

*   hugo new site myblog
*   hugo &ndash;theme=dimension &ndash;baseUrl=&ldquo;[https://lxiuaanng.github.io/&quot;](https://lxiuaanng.github.io/%22) &ndash;buildDrafts
*   cd p&hellip;.
*   git init
*   git add .
*   git commit -m &ldquo;第一次提交&rdquo;
*   git remote add origin [https://github.com/lxiuaunng/lxiuaunng.github.io.git](https://github.com/lxiuaunng/lxiuaunng.github.io.git)
*   git push -u origin master
*   git remote -v &nbsp;&nbsp;&nbsp;/*查看当前通道*/
*   git remote set-url origin [git@github.com](mailto:git@github.com):lxiuaanng/lxiuaanng.github.io.git &nbsp;&nbsp;&nbsp;/*修改https通道为ssh*/
*   git config &ndash;global &ndash;unset user.name
*   git config &ndash;global &ndash;unset user.email &nbsp;&nbsp;&nbsp;/*删除全局用户名和邮箱*/
*   git config user.name &quot;&rdquo;
*   git config user.email  &ldquo;&quot;&nbsp;&nbsp;&nbsp;/*单独配置用户名和邮箱*/

## 问题1

*   [rejected]        master -&gt; master (fetch first)
error: failed to push some refs to &lsquo;[https://github.com/lxiuaunng/lxiuaunng.github.io.git'](https://github.com/lxiuaunng/lxiuaunng.github.io.git)
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., &lsquo;git pull &hellip;') before pushing again.
hint: See the &lsquo;Note about fast-forwards&rsquo; in &lsquo;git push &ndash;help&rsquo; for details.
*   git pull &ndash;rebase origin master
*   或者git push -f origin master     &nbsp;&nbsp;&nbsp;//强推，删除远仓所有文件，将自己的文件全推上去

* * *

## git 配置

*   git config &ndash;global user.name &lsquo;你的用户名&rsquo;

*   git config &ndash;global user.email &lsquo;[你的邮箱](mailto:lxiuaunng@gmail.com)&rsquo;

* * *

## PDF文件内嵌
***
# 【持续更新中&hellip;&hellip;】
