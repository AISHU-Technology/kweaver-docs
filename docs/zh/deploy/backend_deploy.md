# 后端部署

## 准备工作

- 已安装Golang环境
- 已安装Python3环境
- 已安装MySQL和NebulaGraph数据库
- 已安装Redis或Redis Cluster
- 已安装Opensearch
- 已安装MongoDB

## Golang安装

    安装文档 https://golang.google.cn/doc/install

    从https://golang.org/dl/ 或 https://go.dev/dl/ 下载对应操作系统平台指定的版本即可。

### windows 安装

```
从官网下载 go1.x.y.windows-amd64.msi ，按照安装向导安装
添加环境变量：
    go env -w GO111MODULE=on
    go env -w GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
```

### Linux 安装

```
以下以centos7为例：
1、解压： tar xf go1.20.12.linux-amd64.tar.gz -C /usr/local
2、添加到环境变量PATH，修改$HOME/.profile或/etc/profile文件：
    export GO111MODULE=on
    export GOROOT=/usr/local/data/go
    export PATH=$PATH:$GOROOT/bin
    export GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
    export GOPATH=/usr/local/data/go_path
3、加载环境变量：source $HOME/.profile或/etc/profile
4、查看go环境变量：go env
```

### Mac 安装

```
1、从官网下载双击下载的.pkg文件，然后按照向导指示完成安装。
2、配置环境变量，vim ~/.zshrc或~/.bash_profile文件：
    export GOROOT=/usr/local/go
    export GOPATH=/Users/xxx/go_path
    export GO111MODULE=on
    export GOPROXY=https://goproxy.cn,direct
    export PATH=$PATH:$GOROOT/bin:$GOPATH

3、创建GOPATH：mkdir /Users/xxx/go_path
4、重新加载zshrc文件：source ~/.zshrc或source ~/.bash_profile
5、验证go环境变量：go env
```

## Python安装

下载地址：（选择3.9.x版本）

    https://www.python.org/downloads
    https://www.python.org/downloads/windows/

### windows 安装
```
1、根据系统位数下载相应的安装包，然后按照向导指示完成安装
2、验证Python版本：python --V 或 python --version
```

### Linux 安装
以下以centos7为例：

centos系统本身默认安装有python2.x，版本x根据不同版本系统有所不同，可通过 python --V 或 python --version 查看系统自带的python版本。
有一些系统命令时需要用到python2，不能卸载。

```
1、下载安装包和安装依赖包
   - 首先安装gcc编译器，gcc有些系统版本已经默认安装，通过  gcc --version 查看，没安装的先安装gcc，yum -y install gcc
   - 安装其它依赖包（注：不要缺少，否则有可能安装python出错）：
        yum install libffi-devel -y
        yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel
2、编译安装步骤：
   - 下载源码包：wget https://www.python.org/ftp/python/3.9.16/Python-3.9.16.tgz
   - 解压源码包：tar -zxvf Python-3.9.16.tgz
   - 进入源码包目录：cd Python-3.9.16
   - 配置：./configure --prefix=/usr/local/python3  --enable-optimizations
   - 编译：make
   - 安装：make install
   - 建立软连接：ln -sf /usr/local/python3/bin/python3.9 /usr/bin/python
   - 验证：python3 -V
   - 验证pip3：pip3 -V
   - 配置pip3：pip3 config set global.index-url https://mirrors.aliyun.com/pypi/simple/
3、配置环境变量：
   - vim ~/.bashrc或~/.zshrc文件：
        export PATH=$PATH:/usr/local/python3/bin
        export PYTHONPATH=/usr/local/python3/lib/python3.9/site-packages
   - 重新加载环境变量：source ~/.bashrc或source ~/.zshrc
4、验证python版本：python3 -V
```

### 3、Mac 安装

```
1、下载安装包，然后按照向导指示完成安装
2、验证Python版本：python3 --V 或 python3 --version
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
