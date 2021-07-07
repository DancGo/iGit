文档 https://docs.docker.com/
镜像  https://hub.docker.com/

### 卸载 旧版本docker
```bash
sudo yum remove docker \
		  docker-client \
		  docker-client-latest \
		  docker-common \
		  docker-latest \
		  docker-latest-logrotate \
		  docker-logrotate \
		  docker-engine
```

### 设置镜像下载位置
```bash
sudo yum install -y yum-utils
```
```bash
sudo yum-config-manager \
	--add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

### 安装
```bash
sudo yum install docker-ce docker-ce-cli containerd.io
```

### 启动
```bash
sudo systemctl start docker
```

### 开机启动
```bash
sudo systemctl enable docker
```

### 国内服务器开启阿里云容器镜像服务
```bash
sudo mkdir -p /etc/docker
```

```bash
sudo tee /etc/docker/daemon.json <<-'EOF' 
{ "registry-mirrors": ["https://a4jld4q9.mirror.aliyuncs.com"] } 
EOF
```

```bash
sudo systemctl daemon-reload
```

```bash
sudo systemctl restart docker
```
