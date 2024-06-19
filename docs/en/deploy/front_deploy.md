# 前端部署

前端部署指的是将前端代码部署到服务器上，让用户通过浏览器访问。

## 部署方式

前端部署有很多种方式，比如：

- 静态部署：将前端代码编译成静态文件，直接部署到服务器上，用户通过浏览器访问。
- 动态部署：将前端代码编译成动态文件，如 Node.js 应用，部署到服务器上，用户通过浏览器访问。
- 前后端分离部署：将前端代码部署到 CDN（Content Delivery Network，内容分发网络），后端通过 API 接口访问。
- 基于 Docker 的部署：将前端代码编译成 Docker 镜像，部署到 Docker 容器中。
- 基于 Kubernetes 的部署：将前端代码编译成 Kubernetes 镜像，部署到 Kubernetes 集群中。

本文将介绍静态部署、动态部署、前后端分离部署的原理和优缺点。

### 静态部署

静态部署是指将前端代码编译成静态文件，直接部署到服务器上，用户通过浏览器访问。

静态部署方式有很多种，比如：

- 直接将编译后的静态文件部署到服务器上，如 Apache、Nginx 服务器。
- 将编译后的静态文件部署到 CDN（Content Delivery Network，内容分发网络），用户通过 CDN 访问。
- 将编译后的静态文件部署到对象存储（Object Storage，如 Amazon S3、阿里云 OSS），用户通过对象存储访问。

静态部署方式的优点是简单、快速，缺点是不灵活，无法满足动态更新的需求。

### 动态部署

动态部署是指将前端代码编译成动态文件，如 Node.js 应用，部署到服务器上，用户通过浏览器访问。

动态部署方式有很多种，比如：  

- 将 Node.js 应用部署到服务器上，通过 Node.js 服务器运行。
- 将 Node.js 应用部署到云服务器，如 AWS EC2、阿里云 ECS。
- 将 Node.js 应用部署到容器服务，如 Docker、Kubernetes。

动态部署方式的优点是灵活、可靠，可以满足动态更新的需求，缺点是复杂、耗时。

### 前后端分离部署

- 前后端分离部署是指将前端代码部署到 CDN（Content Delivery Network，内容分发网络），后端通过 API 接口访问。
- 前后端分离部署的优点是简单、快速，缺点是不灵活，无法满足动态更新的需求。

### Docker 部署

- Docker 部署是指将前端代码编译成 Docker 镜像，部署到 Docker 容器中。
- Docker 部署的优点是简单、快速，缺点是不灵活，无法满足动态更新的需求。

### Kubernetes 部署
- Kubernetes 部署是指将前端代码编译成 Kubernetes 镜像，部署到 Kubernetes 集群中。
- Kubernetes 部署的优点是灵活、可靠，可以满足动态更新的需求，缺点是复杂、耗时。
- k8s前端示例yml文件：
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend
  labels:
    app: frontend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: frontend
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
      - name: frontend
        image: nginx:latest
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: frontend
  labels:
    app: frontend
spec:
  type: NodePort
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30000
  selector:
    app: frontend
```


## Linux 下 Node 安装

```
更新服务器镜像源：sudo apt-get update
安装 Node.js：sudo apt-get install nodejs
版本查看 ：node -v
node全局模块安装：npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm 版本查看：cnpm -v
cnpm 全局模块安装：cnpm install -g xxx
cnpm 全局模块卸载：cnpm uninstall -g xxx

```

## Windows 下 React 安装
```
下载安装包：https://nodejs.org/zh-cn/download/
下载完成后，双击安装包进行安装。
安装过程中，勾选安装目录，点击下一步。
等待安装完成。
点击安装完成后，在开始菜单中找到 Node.js 并打开。
在命令行中输入 node -v 验证是否安装成功
在命令行中输入 npm -v 验证是否安装成功
在命令行中输入 npm install -g create-react-app 安装 create-react-app
验证是否安装成功：在命令行中输入 create-react-app -V
创建 React 项目：在命令行中输入 create-react-app my-app
进入项目目录：cd my-app
启动项目：npm start
构建项目：npm run build
```

## React 安装

```
初始化：npm install -g create-react-app
创建 React 项目：create-react-app my-app
进入项目目录：cd my-app
启动项目：npm start
编译项目：npm run build
```

## 部署 React 项目

```
编译项目： npm run build
将编译后的静态文件部署到服务器上，如 Apache、Nginx 服务器。sudo cp -r build/* /var/www/html
启动 Apache 服务：sudo systemctl start apache2
访问项目：http://localhost

```

## 部署 Node.js 项目

```
将 Node.js 应用部署到服务器上，通过 Node.js 服务器运行。npm start
访问项目 http://localhost:3000
```

## 后续

本文介绍了前端部署的原理和三种部署方式，并通过 React 项目的安装和部署进行了实践。

前端部署还有很多种方式，比如：

- 基于 Serverless 的部署：将前端代码编译成 Serverless 函数，部署到云函数平台中。
- 基于微前端的部署：将前端代码部署到多个子应用中，通过路由规则实现不同子应用之间的切换。

更多尽情期待。。。