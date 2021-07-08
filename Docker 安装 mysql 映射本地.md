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