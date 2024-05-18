# Docker GPU 部署

## 介绍
 本文档介绍如何在 GPU 上部署 Paddle Serving。

## 环境准备

- 已安装 Docker
- 已安装 NVIDIA Docker
- 已安装 KWeaver


## 部署方式

本文档介绍如何在 GPU 上部署 M3e 服务。

### 1. 构建镜像

KWeaver 提供了 Docker 镜像，可以方便地在 GPU 上部署 M3e 服务。

```
docker build -t paddleserving/serving:gpu-latest -f Dockerfile.gpu .
```

### 2. 启动容器

```
nvidia-docker run -p 9292:9292 --runtime=nvidia -v $PWD/serving_model:/models paddleserving/serving:gpu-latest
```

其中，`-p 9292:9292` 将容器的 9292 端口映射到主机的 9292 端口，`-v $PWD/serving_model:/models` 将当前目录下的 `serving_model` 目录挂载到容器的 `/models` 目录，这样容器内的模型文件可以被访问到。

### 3. 验证

在浏览器中输入 `http://localhost:9292/docs/index.html` 验证是否部署成功。

linux GPU 部署方式与 cpu 部署方式相同，不同之处在于启动容器时增加 `--runtime=nvidia` 参数，指定运行在 nvidia-docker 环境下。

