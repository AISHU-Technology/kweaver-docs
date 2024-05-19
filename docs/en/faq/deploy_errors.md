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

