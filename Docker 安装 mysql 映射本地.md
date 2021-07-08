### [[Docker 安装]]

### 安装数据库

##### 1. 拉取镜像
```bash
sudo docker pull mysql:latest
```

```bash
sudo docker images   #查看一下镜像拉取是否成功
```
![[photo/Pasted image 20210708114010.png]]

##### 2. 运行容器
```bash
sudo docker run -d -p 33060:3306 -e MYSQL_ROOT_PASSWORD=123456 --name mysql mysql:latest
```

```bash
sudo docker ps
#查看容器是否正常运行，没有的话可以用 docker ps -a 查看是否创建容器
#然后用 docker logs 容器ID来查看日志
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

```bash
pid-file       #设置包含运行的named守护进程的进程id的文件位置。
socket 		   #MySQL的通讯协议的载体
datadir		   #MySQL的数据库文件所在目录
log-error	   #MySQL的错误日志
```

### 通过映射让容器内的配置文件、日志文件、数据文件与本地相对应

##### 1. 在本地创建对应文件及目录
```bash
sudo docker rm -f 容器ID
```

```bash
sudo mkdir -p /opt/app/mysql
```
```bash
sudo cd /opt/app/mysql
```
touch my.cnf             #编写配置文件，在下面

mkdir -p /opt/data/mysql
mkdir -p /opt/logs/mysql
cd /opt/logs/mysql
touch error.log
————————————————
版权声明：本文为CSDN博主「A zz」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/weixin_44033360/article/details/106421533