### 2-1. 获取jenkins部署的repo


```
sudo mkdir -p /home/workspaces

cd /home/workspaces

sudo git clone https://github.com/msupers/jenkins-notes.git

cd jenkins-notes/jenkins

```

### 2-2. 了解docker-compose.yml含义（可选）

```
version: '3'
services:
    jenkins:
        # docker 镜像，从docker hub 网站获取 lts代表是长期支持版本
        image: "jenkins/jenkins:2.235.5-lts-centos7"
        # 容器名字前缀，注意有多个docker-compose服务时候不要重复
        container_name: "jenkins-master"
        # 机器重启时，拉起容器
        restart: always
        # 容器里启动服务的命令使用root账号
        user: root
        # jenkins容器的数据持久化到docker-compose.yml 所在文件夹
        volumes:
            - ./jenkins_home:/var/jenkins_home
            # 让容器里可以调用主机的docker
            - /run/docker.sock:/run/docker.sock
        ports:
            # 通过主机的8080端口访问到容器里的8080服务
            - 8080:8080
        networks:
           extnetwork:
# 容器内部ip启动一个私网
networks:
   extnetwork:
      ipam:
         config:
         - subnet: 192.168.168.0/24
```

### 2-3-1. 启动jenkins容器

```
sudo docker-compose up -d 
```

### 2-3-2. 停止jenkins容器

```
sudo docker-compose down
```

### 2-4. 确认容器状态

```
sudo docker ps 
```

![](../_images/2020-11-12_20-10.png)

### 2-5. 获取初始化密码

```
sudo docker logs  
```

![](../_images/2020-11-12_20-11.png)


<!-- ![](../_images/2020-11-13_09-26.gif) -->