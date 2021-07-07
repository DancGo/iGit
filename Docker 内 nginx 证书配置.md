#### docker 容器启动
```bash
sudo docker run -p 80:80 -p 443:443 --restart=always --name nginx -v /mnt/data/nginx/html:/usr/share/nginx/html -v /mnt/data/nginx/logs:/var/log/nginx -v /mnt/data/nginx/conf/:/etc/nginx -d nginx:latest

# -p                    宿主机端口:容器内端口
# --restart=allways     设置自动启动
# --name                新建容易名称
# -v                    宿主机文件路径:容器内文件路径(建议提前在宿主机创建好对应路径，若无，执行后会自动创建; 容器内路径要指定已存在的位置)
```

#### 证书配置教程
https://help.aliyun.com/document_detail/98728.html?spm=5176.b6927164.help.dexternal.33f356a7nfcgiw

#### Nginx 配置
```bash
server {
    listen 443 ssl;
    #配置HTTPS的默认访问端口为443。
    #如果未在此处配置HTTPS的默认访问端口，可能会造成Nginx无法启动。
    #如果您使用Nginx 1.15.0及以上版本，请使用listen 443 ssl代替listen 443和ssl on。
    server_name bscwfc.com; #需要将yourdomain.com替换成证书绑定的域名。
    root html;
    index index.html index.htm;
    ssl_certificate cert/5692122_bscwfc.com.pem;  #需要将cert-file-name.pem替换成已上传的证书文件的名称。
    ssl_certificate_key cert/5692122_bscwfc.com.key; #需要将cert-file-name.key替换成已上传的证书密钥文件的名称。
    ssl_session_timeout 5m;
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
    #表示使用的加密套件的类型。
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #表示使用的TLS协议的类型。
    ssl_prefer_server_ciphers on;
    location / {
        root /usr/share/nginx/html;  #站点目录。
        index index.html index.htm;
    }
}

server {
    listen 80;
    server_name bscwfc.com; #需要将yourdomain.com替换成证书绑定的域名。
    rewrite ^(.*)$ https://$host$1; #将所有HTTP请求通过rewrite指令重定向到HTTPS。
    location / {
        index index.html index.htm;
    }
}
```