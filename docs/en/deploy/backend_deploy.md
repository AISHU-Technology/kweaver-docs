# 后端部署

## 前提条件

- 已安装Golang环境
- 已安装Python3环境
- 已安装MySQL或NebulaGraph数据库
- 已安装Redis或Redis Cluster
- 已安装Opensearch
- 已安装MongoDB

## 准备工作 

- 下载代码
- 配置数据库
- 配置Redis
- 配置Opensearch
- 配置MongoDB
- 配置Celery
- 配置NebulaGraph
- 配置向量服务
- 启动服务
- 启动Celery任务


## 一、Golang安装
安装文档 https://golang.google.cn/doc/install

从https://golang.org/dl/ 或 https://go.dev/dl/ 下载对应操作系统平台指定的版本即可。

### 1、windows 安装
#### 1.1 从官网下载 go1.x.y.windows-amd64.msi ，按照安装向导安装

#### 1.2 添加环境变量
```
go env -w GO111MODULE=on
go env -w GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
```

### 2、Linux 安装
以下以centos7为例：

#### 2.1 解压
```
tar xf go1.20.12.linux-amd64.tar.gz -C /usr/local
```

#### 2.2 添加到环境变量PATH，修改$HOME/.profile或/etc/profile
```
export GO111MODULE=on
export GOROOT=/usr/local/data/go
export PATH=$PATH:$GOROOT/bin
export GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
export GOPATH=/usr/local/data/go_path
```

#### 2.3 加载环境变量
```
source $HOME/.profile或/etc/profile
```
#### 2.4 查看go环境变量
```
go env
```

### 3、Mac 安装
#### 3.1 双击下载的.pkg文件，然后按照向导指示完成安装。
#### 3.2 配置环境变量
```
vim ~/.zshrc

export GOROOT=/usr/local/go
export GOPATH=/Users/xxx/go_path
export GO111MODULE=on
export GOPROXY=https://goproxy.cn,direct
export PATH=$PATH:$GOROOT/bin:$GOPATH

# 创建GOPATH
mkdir /Users/xxx/go_path
```
#### 3.3 重新加载zshrc文件
```
source ~/.zshrc
```
## 二、Python安装
下载地址：（选择3.9.x版本）

https://www.python.org/downloads
https://www.python.org/downloads/windows/

### 1、windows 安装
#### 1.1 根据系统位数下载相应的安装包，然后按照向导指示完成安装
#### 1.2 验证Python版本
```
python -V
```
### 2、Linux 安装
以下以centos7为例：

centos系统本身默认安装有python2.x，版本x根据不同版本系统有所不同，可通过 python --V 或 python --version 查看系统自带的python版本。
有一些系统命令时需要用到python2，不能卸载。
#### 2.1 安装依赖包

1）首先安装gcc编译器，gcc有些系统版本已经默认安装，通过  gcc --version  查看，没安装的先安装gcc，yum -y install gcc

2）安装其它依赖包（注：不要缺少，否则有可能安装python出错）
```
yum install libffi-devel -y
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel
```
#### 2.2、编译安装 
```
wget https://www.python.org/ftp/python/3.9.16/Python-3.9.16.tgz
tar -zxvf Python-3.9.16.tgz
cd Python-3.9.16

./configure --prefix=/usr/local/python3  --enable-optimizations
make 
make install
ln -sf /usr/local/python3/bin/python3.9 /usr/bin/python
 
python3 -V
```
注意：python 没有指向python3 或者说python3.9的

检查python和python3
```
which python
which python3

whereis python 或者whereis python3 也可以检查
```
检查 pip3 和pip
```
which pip3 
which pip

默认没有pip命令，所以还要建立连接一下，yum install pip就有
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
ln -s /usr/local/python3/bin/pip /usr/bin/pip
```
### 3、Mac 安装
#### 3.1 根据操作系统相应的安装包，然后按照向导指示完成安装
#### 3.2 验证Python版本
```
python3 -V
```
## 三、环境变量配置
```
CELERY_CONCURRENCY=4

# nebula 配置
GRAPHDB_HOST=10.4.108.9
GRAPHDB_PASSWORD=nebula
GRAPHDB_PORT=9669
GRAPHDB_READ_ONLY_PASSWORD=nebula
GRAPHDB_READ_ONLY_USER=anydata
GRAPHDB_TYPE=nebulaGraph
GRAPHDB_USER=root

# mongodb 配置
MONGODBAUTHSOURCE=anyshare
MONGODBHOST=10.4.108.9
MONGODBPASS=eisoo.com123
MONGODBPORT=28000
MONGODBUSER=anyshare

# opensearch 配置
OPENSEARCH_HOST=10.4.108.9
OPENSEARCH_PASS=eisoo.com123
OPENSEARCH_PORT=9200
OPENSEARCH_USER=admin

# mysql 配置
DB_TYPE=mysql
RDSDBNAME=anydata
RDSHOST=127.0.0.1
RDSPASS=root
RDSPORT=3306
RDSUSER=root

#redis 配置
REDISCLUSTERMODE=master-slave
REDISHOST=127.0.0.1
REDISPASS=
REDISPORT=6379
REDISREADHOST=127.0.0.1
REDISREADPASS=
REDISREADPORT=6379
REDISREADUSER=
REDISUSER=
REDISWRITEHOST=127.0.0.1
REDISWRITEPASS=
REDISWRITEPORT=6379
REDISWRITEUSER=
SENTINELMASTER=mymaster
SENTINELPASS=eisoo.com123
SENTINELUSER=root

#向量地址
VECTOR_URL=http://10.4.118.205:8302/v1/embeddings
```