---
title: win10配置多个github仓库
author: Lxuan
description: 初步学习git相关的用法，没人带队真的太难受了，很容易做错很多事，就比如这篇文章，不光config配置错误，连整篇md文件都写的乱七八糟，实在是不忍直视.
tags: win10+多仓库配置
toc: true
comments: true
mathjax: false
mathjax2: false
abbrlink: 24538
date: 2021-05-09 00:00:00
cover_picture:
keywords:
top:
categories:
---


初步学习git相关的用法，没人带队真的太难受了，很容易做错很多事，就比如这篇文章，不光config配置错误，连整篇md文件都写的乱七八糟，实在是不忍直视.
<!-- more -->
* * *

**1.** 首先，呃可能并没有首先，因为我这些话没有先后。当我在csdn搜索该类关键词的时候，确实会出来很多文章，但是都是些git的基础文章，比如：  

```
将 
	git config --global user.name
	git config --global user.email
重新设置一遍
```
又或者让你将
`ssh-keygen -t rsa -C xxx@email.com`
再来一遍 //我真心觉得这个步骤很臭


随后会生成两个文件 **id_rsa** 和 **id_rsa_pub**，重点来了，所有博主都会让你配置config文件，可事实上在win10系统里这个文件简直就是摆设（个人看法），我不管怎么配置：  
```
  # 配置lxiuaanng
  Host lxiuaanng.github.com
  HostName github.com
  IdentityFile C:\Users\12748\.ssh\id_rsa_aa
  /_又或者 /C/Users/12748/.ssh/id_rsa_aa_/
  PreferredAuthentications publickey
  User lxiuaanng
 
  # 配置lxiuaunng
  Host lxiuaunng.github.com
  HostName github.com
  IdentityFile C:\Users\12748\.ssh\id_rsa_au
  PreferredAuthentications publickey
  User lxiuaunng
```
它就当我这个文件不存在一样，在网上也找到过许多种方法，但几乎都是差不多样子。  

* * *

**2.** 有的命令执行的莫名其妙，同时有些代码无法执行也很莫名其妙：  
```
ssh -T git@lxiuaanng.github.com
ssh -T git@lxiuaunng.github.com
```
这两串命令的反馈都是&quot;Hi lxiuaanng ... &quot;

我甚至搞不懂  
```
git config user.name
git config user.email
```
这两个命令到底在什么路径下执行，明明两个仓库都进行了 **git init** 都分别配置了用户名和邮箱，但是反馈永远都是&quot;Hi lxiuaanng ... &quot;不由得人心生烦躁

* * *

**3.** 解决？解决个锤子，ssh存在的意义就是能够连接多个仓库，虽然在我的win10上不存在了，但是仍然能够单独连接一个仓库，而全局用户名邮箱也能单独连接一个仓库，于是乎，就没有然后了  

`lxiuaunng用ssh; lxiuaanng用全局`

倒是互不干扰，唯一的缺点就是只能连两个仓库了，以后再建一个账户的话就得手动切换**id_rsa**文件
哦对了，win10系统中

> *   **控制面板-&gt;用户账户—&gt;管理你的凭据—&gt;windows凭据（往下拉）-&gt;git:[https://github.com](https://github.com)这里可以更改全局配置**
> 
> 不过我的建议是直接删掉，等到你需要 **git push -u origin master** 的时候，会重新弹出要你验证github的邮箱和密码

* * *

## 【持续更新(吐槽)中......】
