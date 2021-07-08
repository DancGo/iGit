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