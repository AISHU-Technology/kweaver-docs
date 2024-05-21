# 模型 GPU 部署

## 介绍
 本文档介绍如何在 GPU 上部署 M3e 服务。

## 环境准备

- 已安装 Docker
- 已安装 NVIDIA Docker


## 部署方式

### 构建镜像

KWeaver 提供了 Docker 镜像，可以方便地在 GPU 上部署 M3e 服务。

```
docker build -t kweaverai/kw-models-m3e:v0.2.0-arm64:gpu-latest -f Dockerfile  .
```

### Docker 部署GPU

#### 1. 启动容器

```
nvidia-docker run -p 9897:9897 --runtime=nvidia -v $PWD/serving_model:/models kweaverai/kw-models-m3e:gpu-latest
```

其中，`-p 9897:9897` 将容器的 9292 端口映射到主机的 9292 端口，`-v $PWD/serving_model:/models` 将当前目录下的 `serving_model` 目录挂载到容器的 `/models` 目录，这样容器内的模型文件可以被访问到。

#### 2. 验证

在浏览器中输入 `http://localhost:9897/docs/index.html` 验证是否部署成功。

linux GPU 部署方式与 cpu 部署方式相同，不同之处在于启动容器时增加 `--runtime=nvidia` 参数，指定运行在 nvidia-docker 环境下。

### Docker-Compose部署GPU

如果您使用 Docker-Compose 部署，则可以在 docker-compose.yml 文件中增加以下内容：

```
version: '3'
services:
  serving:
    image: "kweaverai/kw-models-m3e:v0.2.0-arm64"
    ports:
      - "9897:9897"
    runtime: nvidia
    volumes:
      - "./serving_model:/models"
    environment:
      - CUDA_VISIBLE_DEVICES=0
```

其中，`runtime: nvidia` 指定运行在 nvidia-docker 环境下，`CUDA_VISIBLE_DEVICES=0` 指定使用的 GPU 卡号。 

然后，在命令行中执行 `docker-compose up -d` 启动服务。

### K8S 部署GPU

如果您使用 k8s 部署，则可以在 k8s 的 yaml 文件中增加以下内容：

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: serving
spec:
  replicas: 1
  selector:
    matchLabels:
      app: serving
  template:
    metadata:
      labels:
        app: serving
    spec:
      containers:
      - name: serving
        image: "kweaverai/kw-models-m3e:v0.2.0-arm64"
        ports:
        - containerPort: 9897
        resources:
          limits:
            nvidia.com/gpu: 1
        volumeMounts:
        - name: model-volume
          mountPath: /models
      volumes:
      - name: model-volume
        hostPath:
          path: /path/to/serving_model
```

其中，`resources.limits.nvidia.com/gpu: 1` 指定使用的 GPU 数量，`volumeMounts` 将当前目录下的 `serving_model` 目录挂载到容器的 `/models` 目录，这样容器内的模型文件可以被访问到。

然后，在命令行中执行 `kubectl apply -f serving.yaml` 启动服务。


## 注意事项

- 请确保您的 GPU 驱动版本与 CUDA 版本匹配。
- 请确保您的 Docker 版本与 nvidia-docker 版本匹配。
- 请确保您的 k8s 集群中有可用的 GPU 资源。



