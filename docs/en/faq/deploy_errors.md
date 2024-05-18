# 部署常见问题

## 1. 部署时出现 `Error: ENOSPC: System limit for number of file watchers reached`

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

## 2. 部署时出现 `Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules'`

这是由于权限问题导致的。解决方法是使用 `sudo` 命令以超级用户身份运行部署命令。

```
sudo npm install hexo-cli -g    

sudo npm install    
```
