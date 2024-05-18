# Docker-Compose部署

Docker-Compose 是 Docker 官方编排（Orchestration）工具，用于定义和运行多容器 Docker 应用。

本文将介绍如何在 Linux、Windows 和 macOS 上安装 docker-compose。

## 准备工作

- 安装 Docker 环境
- 了解 Docker 镜像、容器、仓库概念
- 了解 Docker Compose 基本概念

## windows 安装
### 1、开启hyper-v

- 在控制面板-程序-启动和关闭windows功能窗口

- 勾选hyper-v及hyper-v管理工具和hyper-v平台
- 勾选适用于linux的windows子系统和虚拟机平台
- 重启电脑后在任务管理器中查看虚拟化功能是否已开启

### 2、docker安装
- 桌面版下载地址如下：https://dockerdocs.cn/docker-for-windows/install/index.html
- 下载后直接安装，默认下一步即可，直到安装完成。可以在cmd中，使用docker -v命令判断是否安装成功。
- 在Docker Desktop的docker Engine中修改docker的镜像下载地址：
```
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "debug": false,
  "experimental": false,
  "insecure-registries": [],
  "registry-mirrors": [
    "https://ung2thfc.mirror.aliyuncs.com"
  ]
}
```
- 可以通过docker info命令查看设置是否生效
### 3、docker-compose 安装
Docker Desktop带有docker-compose，不用另外安装
## linux 安装
以下以centos7为例：
### 1、使用 root 权限更新 yum 包
```
yum -y update
```
这个命令不是必须执行的，看个人情况，后面出现不兼容的情况的话就必须update了

注意：
```
yum -y update：升级所有包同时也升级软件和系统内核；
yum -y upgrade：只升级所有包，不升级软件和系统内核
```
### 2、卸载旧版本（如果之前安装过的话）
```
yum remove docker  docker-common docker-selinux docker-engine
```
### 3、安装需要的软件包
yum-util 提供yum-config-manager功能，另两个是devicemapper驱动依赖
```
yum install -y yum-utils device-mapper-persistent-data lvm2
```
### 4、设置 yum 源

设置一个yum源，下面两个都可用
```
yum-config-manager --add-repo http://download.docker.com/linux/centos/docker-ce.repo（中央仓库）

yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo（阿里仓库）
```
### 5、选择docker版本并安装
（1）查看可用版本有哪些
```
yum list docker-ce --showduplicates | sort -r
```
（2）选择一个版本并安装：yum install docker-ce-版本号
```
yum -y install docker-ce-18.03.1.ce
#尽量安装最新版本，老版本会出现docker拉取镜像错误missing signature key
yum install -y docker-ce
```
（3）镜像加速配置

在 /etc/docker/daemon.json 中写入如下内容（如果文件不存在请新建该文件）：
```
{"registry-mirrors":["https://reg-mirror.qiniu.com/"]}
```
之后重新启动服务：
```
$ sudo systemctl daemon-reload
$ sudo systemctl restart docker
```
### 6、docker-compose 安装
```
#下载docker-compose文件
curl -L https://github.com/docker/compose/releases/download/1.21.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose

#将文件复制到/usr/local/bin环境变量下面
mv docker-compose /usr/local/bin

#给他一个执行权限
chmod +x /usr/local/bin/docker-compose

#查看是否安装成功
docker-compose -version
```
## mac 安装
### 1、docker 安装
（1）Homebrew  的 Cask 已经支持 Docker for Mac，因此可以很方便的使用 Homebrew Cask 来进行安装：
```
$ brew install --cask --appdir=/Applications docker

==> Creating Caskroom at /usr/local/Caskroom
==> We'll set permissions properly so we won't need sudo in the future
Password:          # 输入 macOS 密码
==> Satisfying dependencies
==> Downloading https://download.docker.com/mac/stable/21090/Docker.dmg
######################################################################## 100.0%
==> Verifying checksum for Cask docker
==> Installing Cask docker
==> Moving App 'Docker.app' to '/Applications/Docker.app'.
&#x1f37a;  docker was successfully installed!
```
在载入 Docker app 后，点击 Next，可能会询问你的 macOS 登陆密码，你输入即可。之后会弹出一个 Docker 运行的提示窗口，状态栏上也有有个小鲸鱼的图标。

（2）镜像加速配置

在任务栏点击 Docker for mac 应用图标-> Perferences...-> Daemon-> Registrymirrors。在列表中填写加速器地址。修改完成之后，点击 Apply&Restart 按钮，Docker 就会重启并应用配置的镜像地址了。

### 2、docker-compose 安装
Docker Desktop带有docker-compose，不用另外安装



## 常用命令

- `docker-compose up`：启动所有容器
- `docker-compose down`：停止并删除所有容器
- `docker-compose start`：启动所有容器
- `docker-compose stop`：停止所有容器
- `docker-compose restart`：重启所有容器
- `docker-compose build`：重新构建所有镜像
- `docker-compose ps`：查看所有容器状态
- `docker-compose logs`：查看所有容器日志
- `docker-compose exec`：进入容器

## 示例

假设有一个 `docker-compose.yml` 文件，内容如下：

```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    volumes:
      - ./html:/usr/share/nginx/html
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: test
    ports:
      - "3306:3306"
```

可以用以下命令启动和停止应用：

```
docker-compose up -d
docker-compose down
```


# 参考资料
- [docker-compose 官方文档](https://docs.docker.com/compose/)
- [docker-compose 安装指南](https://docs.docker.com/compose/install/)
- [docker-compose 常用命令](https://docs.docker.com/compose/reference/overview/)

