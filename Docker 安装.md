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