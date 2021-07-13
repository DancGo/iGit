### [[Docker 安装]]

### 安装数据库

##### 1. 拉取镜像
```bash
sudo docker pull mysql:5.7
```

```bash
sudo docker images   #查看一下镜像拉取是否成功
```
![[photo/Pasted image 20210708114010.png]]

##### 2. 运行容器
```bash
sudo docker run -d -p 33060:3306 -e MYSQL_ROOT_PASSWORD=123456 --name mysql mysql:5.7
```

```bash
sudo docker ps
#查看容器是否正常运行，没有的话可以用 docker ps -a 查看是否创建容器
#然后用 docker logs 容器ID 来查看日志
```
![[photo/Pasted image 20210708114232.png]]

##### 3. 查看各个文件所在的位置
```bash
sudo docker exec -it mysql /bin/bash    #进入容器
```

```bash
sudo cat /etc/mysql/mysql.conf.d/mysqld.cnf  #查看各个文件的位置
```

![[photo/Pasted image 20210708114442.png]]

![test][photo/Pasted image 20210708114442.png]

```bash
pid-file       #设置包含运行的 named 守护进程的进程 id 的文件位置。
socket 		   #MySQL 的通讯协议的载体
datadir		   #MySQL 的数据库文件所在目录
log-error	   #MySQL 的错误日志
```

### 通过映射让容器内的配置文件、日志文件、数据文件与本地相对应

##### 1. 在本地创建对应文件及目录
```bash
sudo docker rm -f 容器ID
```

```bash
sudo mkdir -p /opt/app/mysql
sudo cd /opt/app/mysql
sudo touch my.cnf             #编写配置文件,在下面
sudo mkdir -p /opt/data/mysql
sudo mkdir -p /opt/logs/mysql
sudo cd /opt/logs/mysql
sudo touch error.log
```

##### 2. 创建容器
```bash
sudo docker run -p 33060:3306 --name mysql \
-v /mnt/date/mysql/logs:/var/log/mysql \
-v /mnt/date/mysql/data:/var/lib/mysql \
-v /mnt/date/mysql/conf:/etc/mysql \
-e MYSQL_ROOT_PASSWORD=123456 \
-d mysql:5.7

## 创建容器成功后查看一下/opt/data/mysql 下是否有文件
sudo docker exec -it mysql /bin/bash

#进入容器查看配置文件是否同步
sudo cat /etc/mysql/my.cnf
```

##### 时区问题
```bash
sudo docker cp /usr/share/zoneinfo/Asia/Shanghai mysql:/etc/localtime
```

##### 设置开机启动
```bash
sudo docker update mysql --restart=always
```
