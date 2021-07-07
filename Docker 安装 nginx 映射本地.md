### [[Docker 安装]]

#### 下载镜像
```bash
sudo docker pull nginx:latest
```

#### 随便启动一个 nginx 实例，只是为了复制出配置
```bash
sudo docker run -p 80:80 -p 443:443 --name nginx -d nginx:latest
```
#### 如果 80 占用了改成其他端口例如
```bash
sudo docker run -p 82:80 -p 443:443 --name nginx -d nginx:latest
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
sudo mv /mnt/data/nginx/conf/nginx/* /mnt/data/nginx/conf/
```
```bash
sudo rm -rf /mnt/data/nginx/conf/nginx
```


#### 终止原容器
```bash
sudo docker stop nginx
```

#### 执行命令删除原容器
```bash
sudo docker rm nginx
```

#### 创建新的Nginx，执行以下命令
```bash
sudo docker run -p 80:80 -p 443:443 --name nginx \ 
-v /mnt/data/nginx/html:/usr/share/nginx/html \ 
-v /mnt/data/nginx/logs:/var/log/nginx \ 
-v /mnt/data/nginx/conf/:/etc/nginx \ -d nginx:latest
```

#### 设置开机启动nginx
```bash
sudo docker update nginx --restart=always
```

