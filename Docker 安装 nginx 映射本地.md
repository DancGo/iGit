### [[Docker 安装]]

下载镜像
```bash
sudo docker pull nginx:latest
```

随便启动一个nginx实例，只是为了复制出配置
```bash
sudo docker run -p80:80 --name nginx -d nginx:latest
```
如果80占用了改成其他端口例如
```bash
sudo docker run -p82:80 --name nginx -d nginx:latest
```
将容器内的配置文件拷贝到/mnt/nginx/conf/ 下