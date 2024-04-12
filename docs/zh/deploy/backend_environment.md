# һ��Golang��װ
��װ�ĵ� https://golang.google.cn/doc/install

��https://golang.org/dl/ �� https://go.dev/dl/ ���ض�Ӧ����ϵͳƽָ̨���İ汾���ɡ�

## 1��windows ��װ
#### 1.1 �ӹ������� go1.x.y.windows-amd64.msi �����հ�װ�򵼰�װ

#### 1.2 ��ӻ�������
```
go env -w GO111MODULE=on
go env -w GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
```

## 2��Linux ��װ
������centos7Ϊ����

#### 2.1 ��ѹ
```
tar xf go1.20.12.linux-amd64.tar.gz -C /usr/local
```

#### 2.2 ��ӵ���������PATH���޸�$HOME/.profile��/etc/profile
```
export GO111MODULE=on
export GOROOT=/usr/local/data/go
export PATH=$PATH:$GOROOT/bin
export GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
export GOPATH=/usr/local/data/go_path
```

#### 2.3 ���ػ�������
```
source $HOME/.profile��/etc/profile
```
#### 2.4 �鿴go��������
```
go env
```
## 3��Mac ��װ
#### 3.1 ˫�����ص�.pkg�ļ���Ȼ������ָʾ��ɰ�װ��
#### 3.2 ���û�������
```
vim ~/.zshrc

export GOROOT=/usr/local/go
export GOPATH=/Users/xxx/go_path
export GO111MODULE=on
export GOPROXY=https://goproxy.cn,direct
export PATH=$PATH:$GOROOT/bin:$GOPATH

# ����GOPATH
mkdir /Users/xxx/go_path
```
#### 3.3 ���¼���zshrc�ļ�
```
source ~/.zshrc
```
# ����Python��װ
���ص�ַ����ѡ��3.9.x�汾��

https://www.python.org/downloads
https://www.python.org/downloads/windows/

## 1��windows ��װ
#### 1.1 ����ϵͳλ��������Ӧ�İ�װ����Ȼ������ָʾ��ɰ�װ
#### 1.2 ��֤Python�汾
```
python -V
```
## 2��Linux ��װ
������centos7Ϊ����

centosϵͳ����Ĭ�ϰ�װ��python2.x���汾x���ݲ�ͬ�汾ϵͳ������ͬ����ͨ�� python --V �� python --version �鿴ϵͳ�Դ���python�汾��
��һЩϵͳ����ʱ��Ҫ�õ�python2������ж�ء�
#### 2.1 ��װ������

1�����Ȱ�װgcc��������gcc��Щϵͳ�汾�Ѿ�Ĭ�ϰ�װ��ͨ��  gcc --version  �鿴��û��װ���Ȱ�װgcc��yum -y install gcc

2����װ������������ע����Ҫȱ�٣������п��ܰ�װpython����
```
yum install libffi-devel -y
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel
```
#### 2.2�����밲װ 
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
ע�⣺python û��ָ��python3 ����˵python3.9��

���python��python3
```
which python
which python3

whereis python ����whereis python3 Ҳ���Լ��
```
��� pip3 ��pip
```
which pip3 
which pip

Ĭ��û��pip������Ի�Ҫ��������һ�£�yum install pip����
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
ln -s /usr/local/python3/bin/pip /usr/bin/pip
```
## 3��Mac ��װ
#### 3.1 ���ݲ���ϵͳ��Ӧ�İ�װ����Ȼ������ָʾ��ɰ�װ
#### 3.2 ��֤Python�汾
```
python3 -V
```
# ����������������
```
CELERY_CONCURRENCY=4

# nebula ����
GRAPHDB_HOST=10.4.108.9
GRAPHDB_PASSWORD=nebula
GRAPHDB_PORT=9669
GRAPHDB_READ_ONLY_PASSWORD=nebula
GRAPHDB_READ_ONLY_USER=anydata
GRAPHDB_TYPE=nebulaGraph
GRAPHDB_USER=root

# mongodb ����
MONGODBAUTHSOURCE=anyshare
MONGODBHOST=10.4.108.9
MONGODBPASS=eisoo.com123
MONGODBPORT=28000
MONGODBUSER=anyshare

# opensearch ����
OPENSEARCH_HOST=10.4.108.9
OPENSEARCH_PASS=eisoo.com123
OPENSEARCH_PORT=9200
OPENSEARCH_USER=admin

# mysql ����
DB_TYPE=mysql
RDSDBNAME=anydata
RDSHOST=127.0.0.1
RDSPASS=root
RDSPORT=3306
RDSUSER=root

#redis ����
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

#������ַ
VECTOR_URL=http://10.4.118.205:8302/v1/embeddings
```