# centos7安装docker

## 官方文档

[docker官方文档]([Install Docker Engine on CentOS | Docker Documentation](https://docs.docker.com/engine/install/centos/))

## 安装

1. 进入 centos7 系统，可以是虚拟机也可以是云服务器

   * xshell 连接 linux 云服务器

     ![[assets/centos7安装docker/image-20220521012250445.png]]

2. 进入终端，输入以下命令，删除以前安装的 docker （若是之前没有安装过可以不执行）

```linux
$ sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

3. 安装 yum-utils 用以使用 yum-config-manager

```linux
$ sudo yum install -y yum-utils
```

4. 配置官方docker repo（也可以换成阿里云）

```linux
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

5. 安装最新版 docker

```linux
$ sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

![[assets/centos7安装docker/image-20220521012322792.png]]



![[assets/centos7安装docker/image-20220521012336101.png]]



安装过程中需要按“y”来下一步，请核对终端中指纹是否和官网中的一致。（一般不可能不一致）

## 启动

1. 启动 docker

```linux
$ sudo systemctl start docker //静默启动
$ sudo systemctl status docker //启动docker，并查看docker服务状态
$ sudo systemctl enable docker //开机自启动
$ sudo systemctl stop docker //停止服务
```

2. docker 容器自动启动

```
# 开启容器自启动
docker update --restart=always "容器名"
例如：docker update --restart=always tracker

# 关闭容器自启动
docker update --restart=no"容器名"
例如：docker update --restart=no tracker

##### 相关配置解析
no：
    不要自动重启容器。（默认）

on-failure： 
    如果容器由于错误而退出，则重新启动容器，该错误表现为非零退出代码。

always：
    如果容器停止，请务必重启容器。如果手动停止，则仅在Docker守护程序重新启动或手动重新启动容器本身时才重新启动。（参见重启政策详情中列出的第二个项目）

unless-stopped：
    类似于always，除了当容器停止（手动或其他方式）时，即使在Docker守护程序重新启动后也不会重新启动容器。
```

## 卸载

1. 卸载 docker 

```
# 卸载 docker 引擎、 CLI、 Containerd 和 Docker 组合包
$ sudo yum remove docker-ce docker-ce-cli containerd.io

# 删除目录（注意保存重要数据）
$ sudo rm -rf /var/lib/docker
$ sudo rm -rf /var/lib/containerd
```
