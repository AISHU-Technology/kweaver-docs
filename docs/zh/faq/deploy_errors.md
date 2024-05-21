# 部署常见问题

## Linux 常见问题
### 部署时出现 `Error: ENOSPC: System limit for number of file watchers reached`

这是由于系统限制了文件监视器的数量，导致无法监视文件变化。解决方法是增加文件监视器的数量。

在 Linux 系统上，可以通过修改 `/etc/sysctl.conf` 文件，增加以下配置：

```
fs.inotify.max_user_watches=524288
```

524288 是推荐的最大值，可以根据实际情况调整。

然后执行 `sysctl -p` 命令使配置生效。

在 macOS 系统上，可以通过运行以下命令来增加文件监视器的数量：

```
sudo sysctl -w kern.maxfiles=524288
sudo sysctl -w kern.maxfilesperproc=524288
```

其中 `524288` 是推荐的最大值，可以根据实际情况调整。

### 部署时出现 `Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules'`

这是由于权限问题导致的。解决方法是使用 `sudo` 命令以超级用户身份运行部署命令。

```
sudo npm install hexo-cli -g    

sudo npm install    
```

### 如何查看 CPU 信息？

在容器中执行 `lscpu` 命令可以查看 CPU 信息。

### 如何查看内存信息？

在容器中执行 `free -m` 命令可以查看内存信息。

### 如何查看磁盘信息？

在容器中执行 `df -h` 命令可以查看磁盘信息。

### 如何查看网络信息？

在容器中执行 `ifconfig` 命令可以查看网络信息。

### 如何查看路由信息？

在容器中执行 `route -n` 命令可以查看路由信息。

### 如何查看进程信息？

在容器中执行 `ps aux` 命令可以查看进程信息。

### 如何查看端口占用情况？

在容器中执行 `netstat -tlpn` 命令可以查看端口占用情况。


## GPU 常见问题

### 如何查看 GPU 信息？

在容器中执行 `nvidia-smi` 命令可以查看 GPU 信息。

### 如何查看 GPU 占用率？

在容器中执行 `nvidia-smi` 命令，在 `Processes` 部分可以查看 GPU 占用率。

### 如何查看 GPU 内存占用情况？

在容器中执行 `nvidia-smi` 命令，在 `Memory` 部分可以查看 GPU 内存占用情况。

### 如何查看 GPU 显存占用情况？

在容器中执行 `nvidia-smi` 命令，在 `Utilization` 部分可以查看 GPU 显存占用情况。

### 如何查看 GPU 进程信息？

在容器中执行 `nvidia-smi` 命令，在 `Processes` 部分可以查看 GPU 进程信息。

### 如何查看 GPU 显存信息？

在容器中执行 `nvidia-smi` 命令，在 `GPU` 部分可以查看 GPU 显存信息。

### 如何查看 GPU 驱动版本？

在容器中执行 `nvidia-smi` 命令，在 `Driver Version` 部分可以查看 GPU 驱动版本。

### 如何查看 GPU 设备数量？

在容器中执行 `nvidia-smi` 命令，在 `Attached GPUs` 部分可以查看 GPU 设备数量。

### 如何安装 CUDA ？

1. 下载 CUDA 11.4 运行时库：

   ```
   wget https://developer.download.nvidia.com/compute/cuda/11.4.0/local_installers/cuda_11.4.0_470.42.01_linux.run
   ```

2. 运行安装脚本：

   ```
   chmod +x cuda_11.4.0_470.42.01_linux.run
   ./cuda_11.4.0_470.42.01_linux.run --silent --toolkit
   ```

3. 在容器中安装 CUDA 驱动：

   ```
   apt-get update && apt-get install cuda-drivers
   ```

4. 验证 CUDA 驱动是否安装成功：

   ```
   nvidia-smi
   ```

### 如何安装 cuDNN ？

1. 下载 cuDNN 8.2.4 运行时库：

   ```
   wget https://developer.download.nvidia.com/compute/redist/cudnn/v8.2.4/cudnn-11.4-linux-x64-v8.2.4.30.tgz
   ```

2. 解压运行库：

   ```
   tar -xzvf cudnn-11.4-linux-x64-v8.2.4.30.tgz
   ```

3. 复制运行库到容器：

   ```
   sudo cp cuda/include/cudnn*.h /usr/local/cuda/include
   sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
   sudo chmod a+r /usr/local/cuda/include/cudnn*.h /usr/local/cuda/lib64/libcudnn*
   ```

4. 验证 cuDNN 运行库是否安装成功：

   ```
   ldd /usr/local/cuda/lib64/libcudnn.so.8.2.4
   ```  
   
5. 验证 cuDNN 运行库版本是否正确：

   ```
   cat /usr/local/cuda/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
   ```


## Docker 常见问题

### 如何查看 Docker 版本？

在容器中执行 `docker version` 命令可以查看 Docker 版本。

### 如何查看 Docker 镜像？

在容器中执行 `docker images` 命令可以查看 Docker 镜像。

### 如何查看 Docker 容器？

在容器中执行 `docker ps -a` 命令可以查看 Docker 容器。

### 如何查看 Docker 容器日志？

在容器中执行 `docker logs <container_name>` 命令可以查看 Docker 容器日志。

### 如何查看 Docker 容器网络信息？

在容器中执行 `docker network ls` 命令可以查看 Docker 容器网络信息。

### 如何查看 Docker 容器磁盘信息？

在容器中执行 `docker system df` 命令可以查看 Docker 容器磁盘信息。

### 如何查看 Docker 容器资源限制？

在容器中执行 `docker inspect <container_name>` 命令可以查看 Docker 容器资源限制。

### 如何查看 Docker 容器资源使用情况？

在容器中执行 `docker stats` 命令可以查看 Docker 容器资源使用情况。

### 如何查看 Docker 容器资源限制？

在容器中执行 `docker inspect <container_name>` 命令可以查看 Docker 容器资源限制。


## 容器常见问题
### 如何查看容器内的内存占用情况？

在容器中执行 `free -m` 命令可以查看容器内的内存占用情况。

### 如何查看容器内的磁盘占用情况？

在容器中执行 `df -h` 命令可以查看容器内的磁盘占用情况。

### 如何查看容器内的网络流量？

在容器中执行 `iftop` 命令可以查看容器内的网络流量。

### 如何查看容器内的磁盘 IO？

在容器中执行 `iotop` 命令可以查看容器内的磁盘 IO。

### 如何查看容器内的网络连接情况？

在容器中执行 `ss -tulp` 命令可以查看容器内的网络连接情况。

### 如何查看容器内的网络连接信息？

在容器中执行 `netstat -tulp` 命令可以查看容器内的网络连接信息。

### 如何查看容器内的路由信息？

在容器中执行 `route -n` 命令可以查看容器内的路由信息。

### 如何查看容器内的磁盘 IO 信息？

在容器中执行 `iostat -x 1` 命令可以查看容器内的磁盘 IO 信息。

### 如何查看容器内的 CPU 信息？

在容器中执行 `lscpu` 命令可以查看容器内的 CPU 信息。

### 如何查看容器内的 GPU 信息？

在容器中执行 `nvidia-smi` 命令可以查看容器内的 GPU 信息。

### 如何查看容器内的 Docker 信息？

在容器中执行 `docker info` 命令可以查看容器内的 Docker 信息。

### 如何查看容器内的 Docker 镜像信息？

在容器中执行 `docker images` 命令可以查看容器内的 Docker 镜像信息。

### 如何查看容器内的 Docker 容器信息？

在容器中执行 `docker ps -a` 命令可以查看容器内的 Docker 容器信息。

### 如何查看容器内的 Docker 容器日志？

在容器中执行 `docker logs <container_name>` 命令可以查看容器内的 Docker 容器日志。

### 如何查看容器内的 Docker 容器网络信息？

在容器中执行 `docker network ls` 命令可以查看容器内的 Docker 容器网络信息。

### 如何查看容器内的 Docker 容器磁盘信息？

在容器中执行 `docker system df` 命令可以查看容器内的 Docker 容器磁盘信息。

### 如何查看容器内的 Docker 容器资源限制？

在容器中执行 `docker inspect <container_name>` 命令可以查看容器内的 Docker 容器资源限制。

### 如何查看容器内的 Docker 容器资源使用情况？

在容器中执行 `docker stats` 命令可以查看容器内的 Docker 容器资源使用情况。

### 如何查看容器内的 Docker 容器资源限制？

在容器中执行 `docker inspect <container_name>` 命令可以查看容器内的 Docker 容器资源限制。


### 如何查看容器内的进程？

在容器中执行 `ps aux` 命令可以查看容器内的进程。

### 如何查看容器内的端口占用情况？

在容器中执行 `netstat -tlpn` 命令可以查看容器内的端口占用情况。

### 如何在容器中安装 CUDA ？

在容器中执行以下命令安装 CUDA：

```
apt-get update && apt-get install cuda-toolkit-11-4
```

###  如何在容器中安装其他软件？

在容器中执行 `apt-get update && apt-get install <software>` 命令可以安装其他软件。

### 如何在容器中运行 Tensorflow 程序？

在容器中安装 Tensorflow 依赖：

```
apt-get update && apt-get install python3-pip
pip3 install tensorflow
```

然后在容器中运行 Tensorflow 程序：

```
python3 -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
```

### 如何在容器中运行 PyTorch 程序？

在容器中安装 PyTorch 依赖：

```
apt-get update && apt-get install python3-pip
pip3 install torch torchvision
```

然后在容器中运行 PyTorch 程序：

```
python3 -c "import torch; print(torch.rand(5, 3))"
```

## nginx 常见问题

### nginx gzip压缩配置？

```
gzip on; # 开启gzip压缩
gzip_min_length 4k; # 小于4k的文件不会被压缩，大于4k的文件才会去压缩
gzip_buffers 16 8k; # 处理请求压缩的缓冲区数量和大小，比如8k为单位申请16倍内存空间；使用默认即可，不用修改
gzip_http_version 1.1; # 早期版本http不支持，指定默认兼容，不用修改
gzip_comp_level 2; # gzip 压缩级别，1-9，理论上数字越大压缩的越好，也越占用CPU时间。实际上超过2的再压缩，只能压缩一点点了，但是cpu确是有点浪费。因为2就够用了
# 压缩的文件类型 MIME类型
gzip_types text/plain application/x-javascript application/javascript text/javascript text/css application/xml application/x-httpd-php image/jpeg image/gif image/png application/vnd.ms-fontobject font/x-woff font/ttf;# text、早期js、js、js的另一种写法、css、xml、php、jpeg、gif、png、woff字体、ttf字体
gzip_vary on; # 是否在http header中添加Vary: Accept-Encoding，一般情况下建议开启

``` 

### nginx 静态压缩配置？
动态压缩是在服务器上进行的，压缩级别越高越耗性能，静态压缩就是为了解决这个问题而生的，开启静态压缩后，nginx会自动寻找.gz后缀的文件，如果没有则返回源文件；于是乎，我们就可以在前端构建的时候进行gzip压缩；

- nginx.conf 配置静态压缩
```
gzip_static on;
```
- vue.js 项目中配置静态压缩vite-plugin-compression
```
1. npm install vite-plugin-compression -D
2. vite.config.js 配置
import { defineConfig } from 'vite'
import compression from 'vite-plugin-compression'
export default {  
  plugins: [
    compression({
      threshold: 10240, // 压缩大小超过10k才压缩
      algorithm: 'gzip', // 使用gzip压缩
      deleteOriginFile: false // 是否删除源文件
    })
  ]
}  
```
- react.js 项目中配置静态压缩compression-webpack-plugin
```
1. npm install compression-webpack-plugin -D
2. webpack.config.js 配置
const CompressionPlugin = require('compression-webpack-plugin')
module.exports = {
  plugins: [
    new CompressionPlugin({
      test: /\.(js|css|svg|ttf|woff|woff2)$/, // 匹配文件类型
      threshold: 10240, // 压缩大小超过10k才压缩
      deleteOriginalAssets: false // 是否删除源文件
    })
  ]
}
```
- 静态压缩注意事项
```
1. 静态压缩只能压缩静态文件，不能压缩动态文件，所以nginx对静态压缩的文件要求较高，必须与原文件同时生成，如果不是同时生成的，那么nginx将无法进行匹配，导致无法压缩（导致gz文件与原文件时间不一致，导致静态压缩不生效）。
2. nginx默认是没有安装ngx_http_gzip_static_module静态压缩模块的，需手动开启，否则nginx无法识别.gz后缀的文件。
3. 静态压缩的压缩级别越高，压缩率越高，但是压缩时间也越长，所以需要根据实际情况进行调整。
4. 静态压缩的压缩率和压缩时间取决于压缩算法，gzip压缩算法压缩率较高，压缩时间也较短，但是压缩率不如brotli压缩算法，brotli压缩算法压缩率较低，压缩时间也较长。
```

### nginx动静结合
```
1. 实际应用中我们通常会采取静态压缩+动态压缩结合的方式来处理我们的静态资源，静态压缩的优先级会高于动态压缩，并不是说压缩的越到小越好，如果已经进行过静态压缩的文件就没有必要再进行动态压缩了，因为这样浪费性能，得不偿失，所以动态压缩的gzip_min_length这个配置尤为重要，能让我们避免一些无谓的操作；
2. 经过上面一系列操作之后，可以用站长工具测试下压缩的效果，直接将静态资源的连接复制进去即可：https://tool.chinaz.com/Gzips/?q=c.nxw.so
```

### nginx配置sendfile on和gzip共存问题？

```
1. sendfile on; # 开启sendfile，可以直接输出文件内容，不用再经过内核，提高性能
2. sendfile和gzip共存问题是指nginx开启sendfile和gzip后，如果文件大于gzip_min_length，则会先压缩再输出，导致文件大小和gzip压缩后的大小不一致，导致浏览器无法解压，导致文件无法正常显示。解决方法是关闭sendfile，或者修改gzip_min_length，让文件大于gzip_min_length后才压缩。
``` 
