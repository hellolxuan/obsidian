---
title: SQL Server遇到的问题和解决方法
tags: SQL
author: Lxuan
keywords: SQL
abbrlink: 56108
date: 2021-10-15 13:46:37
categories: 技术
toc:
thumbnail:
cover:
---

未在本地计算机上注册“Microsoft.ACE.OLEDB.12.0”提供程序。 (System.Data)
<!--more-->
<br />
我是在使用SQL写作业的时候出现的这个问题，前一天晚上因为office出现了一些小问题，于是重装了一下，但不知道是不是office选择了64位的原因还是其他什么，总之第二天给数据表导入Excel数据的时候弹出以下错误

（弹窗忘了截图了，最显而易见的就是`未在本地计算机上注册“Microsoft.ACE.OLEDB.12.0”提供程序`这句话）

```: 错误提示
TITLE: SQL Server 导入和导出向导
------------------------------  

The operation could not be completed.

------------------------------
ADDITIONAL INFORMATION:

未在本地计算机上注册“Microsoft.ACE.OLEDB.12.0”提供程序。 (System.Data)

------------------------------
BUTTONS:

OK
------------------------------
```
<br />

那么解决方法也很简单
1.首先就是重装office并选择32版本（跟office没有关系就不用管了）
2.其次就是去百度搜索<font color="red">AccessDatabaseEngine</font>这个东西，一般往下翻两下就会有一些好心网站，都是可以下载的

![下载解压后打开一般会有这两个文件](assets/SQL-Server遇到的问题和解决方法/AccessDatabaseEngine.exe.png)

3.上面的是32位的，双击安装，不用非得装C盘，随便一个地方都可以

回到SQL Server，重新导入数据，如果成功了，那么恭喜你可以继续写作业了
如果仍然不能解决，可以尝试卸载32位安装64位，如果还不能解决，建议重装32位的office，然后重复上述操作
如果还还还不能解决，那么问题就有点难度了，建议百度或者CSDN找大神的解决方案

写作业去了，拜拜，希望我能解决您的问题