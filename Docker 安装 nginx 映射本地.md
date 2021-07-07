### [[Docker 安装]]

#### 下载镜像
```bash
sudo docker pull nginx:latest
```

#### 随便启动一个 nginx 实例，只是为了复制出配置
```bash
sudo docker run -p80:80 --name nginx -d nginx:latest
```
#### 如果 80 占用了改成其他端口例如
```bash
sudo docker run -p82:80 --name nginx -d nginx:latest
```
#### 将容器内的配置文件拷贝到 /mnt/data/nginx/conf/ 下
```bash
sudo mkdir -p /mnt/data/nginx/html
```
```bash
sudo mkdir -p /mnt/data/nginx/logs
```
```bash
sudo mkdir -p /mnt/data/nginx/conf
```
```bash
cd /mnt/data/nginx/conf
```
```bash
sudo docker container cp nginx:/etc/nginx .
```
#### 由于拷贝完成后会在 config 中存在一个 nginx 文件夹，所以需要将它的内容移动到 conf 中
```bash
sudo mv /mydata/nginx/conf/nginx/* /mydata/nginx/conf/
```
```bash
sudo rm -rf /mydata/nginx/conf/nginx
```
