---
title: win10配置多个github仓库（下）
author: Lxuan
description: >-
  相比较上一篇文章，这篇算是有了丢丢进步，好歹会写代码块了，md文件还是要多写写，不然很多格式记不住。这篇文章主要纠正了上一篇的错误，以及写明了配置多仓库的正确步骤，有需要就来看一下吧。（ps：config文件建议直接复制我的，以免出现打错字母的情况，不要看我，我没有我不是）
tags: win10+多仓库配置
toc: true
comments: true
mathjax: false
mathjax2: false
abbrlink: 35889
date: 2021-05-29 00:00:00
keywords:
top:
categories:
---

相比较上一篇文章，这篇算是有了丢丢进步，好歹会写代码块了，md文件还是要多写写，不然很多格式记不住。这篇文章主要纠正了上一篇的错误，以及写明了配置多仓库的正确步骤，有需要就来看一下吧。（ps：config文件建议直接复制我的，以免出现打错字母的情况，不要看我，我没有我不是）
<!-- more -->

#### 删除全局配置

```
git config --global --unset user.name   
git config --global --unset user.email   
```
#### 配置此仓库1的用户

```
cd 仓库地址1
git config user.name "xxx"
git config user.email "xxx@xxx.com"  
```
#### 配置此仓库2的用户
```
cd 仓库地址2
git config user.name "xxx"
git config user.email "xxx@xxx.com"   
```
.........   

#### 创建公钥
```
cd ~/.ssh
ssh-keygen -t rsa -C "111@xxx.com" id_rsa_111 
ssh-keygen -t rsa -C "222@xxx.com" id_rsa_222   
//将.pub文件内容添加到GitHub或gitee的ssh管理库中
```
#### 配置config文件
```
cd ~/.ssh
```
新建文件config  
输入
```
# gitee
Host gitee.com
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_gitee
# github
Host 111.github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_111
# github
Host 222.github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_222
```
![[assets/win10配置多个github仓库(下)/image-20220521013509321.png]]


**原因：**  

1. ssh 客户端是通过类似`git@github.com:githubUserName/repName.git`的地址来识别使用本地的哪个私钥的，地址中的 `User` 是@前面的`git`， `Host` 是@后面的`github.com`。
2. 如果所有账号的` User` 和 `Host` 都为 `git` 和 `github.com`，那么就只能使用一个私钥。所以要对`User` 和 `Host` 进行配置，至少让每个账号使用自己的 `Host`，每个 `Host` 的域名做 `CNAME` 解析到 `github.com`，如上面配置中的`111.github.com和222.github.com`。
3. 配置了别名之后，新的地址就是`git@111.github.com:githubUserName/repName.git`（在添加远程仓库时使用）。   

这样 ssh 在连接时就可以区别不同的账号了。
```
ssh -T git@111.github.com
ssh -T git@222.github.com
//测试ssh连接，返回“Hi xxx ...”则成功
```
![[assets/win10配置多个github仓库(下)/image-20220521013525738.png]]



#### 查看远程分支

```
git remote -v     
```
#### 添加远程仓库
```
cd 仓库1地址
git remote add origin git@111.github.com:githubUserName/repName.git

cd 仓库2地址
git remote add origin git@222.github.com:githubUserName/repName.git
```
