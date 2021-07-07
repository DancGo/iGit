#### docker 容器启动
```bash
sudo docker run -p 80:80 -p 443:443 --restart=always --name nginx -v /mnt/data/nginx/html:/usr/share/nginx/html -v /mnt/data/nginx/logs:/var/log/nginx -v /mnt/data/nginx/conf/:/etc/nginx -d nginx:latest```

# -p                    宿主机端口:容器内端口
# --restart=allways     设置自动启动
# --name                新建容易名称
# -v                    宿主机文件路径:容器内文件路径(建议提前在宿主机创建好对应路径，若无，执行后会自动创建; 容器内路径要指定已存在的位置)