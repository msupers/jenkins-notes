### 1-1. 安装centos 7.8 64bit

?>最小化安装

- 略

### 1-2. 安装docker

?> 卸载旧版本docker（可选）

```
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

?>安装yum工具

```
sudo yum install -y yum-utils
```

?>配置docker repo

```
sudo yum-config-manager     --add-repo     https://download.docker.com/linux/centos/docker-ce.repo
```

?>安装docker

```
sudo yum install docker-ce docker-ce-cli containerd.io
```

?>检查、启动、设置重启机器启动

```
systemctl start docker.service

systemctl enable docker.service

docker version

```



### 1-3. 安装docker-compose

?>下载docker-compose

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

?>添加执行权限

```
sudo chmod +x /usr/local/bin/docker-compose
```

?>查看版本

```
docker-compose -v
```



