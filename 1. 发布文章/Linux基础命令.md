---
title: Linux基础命令
tags:
  - 技术
  - Linux
author: Lxuan
toc: true
keywords: Linux
categories: Linux
abbrlink: 60189
date: 2021-12-14 00:00:00
thumbnail:
cover:
top:
---
最基础命令，入门级水平
命令之间相关性差，慎观，慎观。

<!--more-->

[TOC]

### 第一章

1. pwd # 显示当前用户所处目录
2. cd # 在不同的目录中切换
3. ls # 列出该目录下的文件及目录

   > -a # 包括隐藏文件；-t # 依照最后修改时间的顺序列出文件
   >
   > -l # 列出目录下文件好目录的详细信息

4. cat # 查看文件内容

   > cat 文件1 文件2 > 文件3 # 12合并覆盖3
   >
   > cat 文件1 文件2 >> 文件3 # 12合并附加3
   
5. more # 分屏显示，空格向下移动，q建退出
6. less # 回车向下一行，空格向下一页，b向上一页
7. head # 默认只显示前十行

   > -n # 显示前几行
   
8. tail # 显示末尾几行
9. mkdir # 创建目录

   > rmdir # 删除空目录
   
10. touch # 创建文件
11. cp # 复制文件

    > -R # 递归复制
    
12. mv # 文件或目录的移动和重命名
13. rm # 删除

    > -f # 不提示
    
    > -r递归删除
    
14. diff # 比较文件内容的不同
15. ln # 硬链接（两个文件指向同一个存储空间）

    > -s # 软连接（win中的快捷方式）
    
16. gzip # 压缩
17. gunzip # 解压缩
18. tar # 打包

    > tar -cvf 1.tar 2.txt 3.txt
    > 
    > tar -xvf 1.tar
    > 
    > tar -czvf 打包并压缩
    
19. whereis # 可执行文件所在地址
20. grep # 查找文件中指定的字符串
21. ps # 查看系统进程
22. kill # 杀死进程
23. top # 实时监控进程状况
24. bg # 放入后台
25. jobs # 查看后台进程
26. fg # 调到前台
27. who # 查看当前主机用户终端信息

### 第三章

1. echo # 输出字符

   > $hello # 定义变量hello
   >
2. ls -l /tmp > dir # 重定向

   > < 输入重定向
   >
3. | # 管道，结合命令

   > cat /etc/passwd | grep root
   >
4. sh # 执行.sh文件

   > 可执行文件(x)可以用 ./执行文件 来执行
   >
5. vim # vim编辑器

   > a # 插入；esc # 命令模式；wq # 保存并退出
   >
6. chmod # 文件权限修改

   > -r # 可读；4
   >
   > -w # 可写；2
   >
   > -x # 可执行；1
   >
   > 原始权限：rwxrwxrwx 转换数字：(421)(421)(421) 数字表示法： 777
   >
7. chown # 修改文件所属用户

   > chown 用户 : 属组 文件
   >

### 第四章

1. /etc/passwd 文件 # 用户账户及其相关信息（密码除外），所有人可读

   > 用户名：加密口令：UID：GID：用户的描述信息：主目录：命令解释器
   >
2. /etc/shadow 文件 # 存放用户密码，仅root可读

   > 用户名：加密后的用户口令
   >
3. /etc/group 文件 # 用户的组账户信息，所有人可读

   > 组群名称：组群口令（一般为空，用 x 占位）：GID：组群成员列表
   >
4. /etc/gshadow 文件 # 存放组群的加密口令、组管理员等信息，仅root可读

   > 组群名称：加密后的组群口令（没有就！）：组群管理员：成员列表
   >
5. useradd # 新建用户

   > -c # 用户的注释信息
   >
   > -u # 指定用户UID
   >
   > -d # 指定用户主目录
   >
   > -g # 用户所属主组群名称或GID
   >
   > -p psaawd # 加密口令
   >
6. passwd # 设置口令

   > -l 锁定停用账户
   >
   > -u 口令解除
   >
   > -d 口令为空
   >
7. usermod # 修改用户的属性

   > -g # 变更所属用户组
   >
   > -G # 变更扩展用户组；usermod -G root user1
   >
   > -L / -U # 锁定用户 / 解锁用户
   >
   > -u # 修改UID；usermod -u 8888 user1
   >
8. userdel # 删除用户

   > -r # 除/etc/passwd、/etc/shadow、/etc/group、/etc/gshadow中的信息外顺便删除主目录下的所有信息
   >
9. groupadd # 创建组群
10. groupmod # 修改组群

    > -g # 修改组群GID
    >
    > -n # 修改组名
    >
11. gpasswd # 为组群添加用户

    > -a # 把用户加入组；gpasswd -a user1 group1
    >
    > -r # 取消组密码
    >
    > -d # 把用户从组中删除
    >
    > -A # 指派管理员
    >
12. su # 切换用户
13. sudo # 给用户提供额外权限
14. whoami # 我是谁

### 第五章

1. fdisk # 磁盘分区工具

   > fdisk 分区目录 # fdisk /dev/sda 在/dev/sda上分区
   >
   > ：p # 查看分区表
   >
   > ：n # 新建分区
   >
   > ：d # 删除分区表
   >
   > ：q # 不保存退出
   >
   > ：w # 保存修改
   >
2. mount # 挂载

   > mount 设备 挂载目录
   >
3. unmount # 卸载

# 端口开放命令 #端口

CentOS：

1. 防火墙

   systemctl status firewalld.service（查看防火墙状态）

   systemctl stop firewalld.service （关闭防火墙）

   systemctl start firewalld.service （开启防火墙）

   systemctl disable firewalld.service （禁止防火墙自启动）

   systemctl enable firewalld.service （防火墙随系统开启启动）

2. 开放指定端口
   firewall-cmd --zone=public --add-port=6379/tcp --permanent
   命令含义：
   –zone # 作用域
   –add-port=6379/tcp # 添加端口，格式为：端口/通讯协议
   –permanent # 永久生效，没有此参数重启后失效

3. 重启防火墙
   firewall-cmd --reload

4. 查看端口号
   netstat -ntlp //查看当前所有tcp端口·
   netstat -ntulp |grep 6379 //查看所有1935端口使用情况·

