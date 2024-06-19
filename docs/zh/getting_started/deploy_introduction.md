# 部署简介

本章节将介绍如何将KWeaver部署到不同的环境中所需要的软件和硬件条件，以及部署方式和步骤。

## 1、部署环境
KWeaver支持多种部署环境，包括：

- 本地部署
- 云端部署
- 容器化部署
- kubernetes部署

## 2、开发环境支持
- Windows 10
- Linux (AMD64、ARM64)
- Docker 24.0.6

## 3、服务器硬件资源
- 操作系统：Ubuntu 20.04、GPU服务器
- CPU：8核及以上
- 内存：16GB及以上
- 硬盘：40GB及以上
- 网络：需要能够访问外网

## 4、依赖开发语言
- Python >= 3.9
- Go >= 1.20
- Node >= 18.12.1
- React >= 18.2.0
- Ant-Design >= 4.18.7
- G6 >= 4.8.7
- Webpack >= 5.5.0

## 5、依赖中间件
- Mysql >= 8.0.27 系统配置持久化
- MongoDB >= 4.0.27 图谱数据存储中间数据存储
- Redis >= 7.0.4 缓存和消息队列中间件
- OpenSearch >= 2.12.0 知识图谱检索、大模型向量检索和本地知识库
- Nebula >= 3.6.0 图数据存储
- Nginx >= 1.24.1 反向代理和负载均衡


## 6、安装部署

- 下载代码并启动docker-compose
```bash
 git clone https://github.com/AISHU-Technology/kweaver.git
 cd kweaver/docker
 docker-compose up -d
```

- 启动成功后，访问http://localhost:8080 进入KWeaver主页


## 7、部署注意事项

- 数据库初始化脚本

```
1、初始化mysql数据库脚本: mysql_init.sql
2、创建nebula用户和授权:
    - 登录http://xx.xx.xx.xx:7001 并执行创建用户脚本:
    - CREATE SPACE kweaver(partition_num=10, replica_factor=1, vid_type=FIXED_STRING(30));
    - CREATE USER IF NOT EXISTS kweaver WITH PASSWORD 'Kw1ea2ver!3';
    - GRANT ROLE ADMIN ON kweaver TO kweaver;
```

- 部署向量模型
```
KWeaver支持向量模型的部署，用于图谱构建时结合向量模型构建本地知识库，用于大模型记忆和向量相似检索；分为两种方式：
外连模型：添加kw-builder环境变量VECTOR_URL向量模型（M3E）连接地址
内置模型：下载M3E模型放入kw和下载kw-models-m3e镜像，启动容器时添加环境变量VECTOR_URL指向向量服务中。
  - 1、使用kw-models-m3e镜像中微调后的模型(支持GPU、CPU),GPU支持类型cuda和mps。下载镜像地址：docker pull kweaverai/kw-models-m3e:v0.2.0-arm64或docker pull kweaverai/kw-models-m3e:v0.2.0-amd64
  - 2、在modelscope、huggingface.co中下载M3E模型放入kw-models-m3e/models下进行使用
```


更新中，敬请期待。。。