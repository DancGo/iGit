#### 首先下载 java sdk 包
[当前流程为 jdk8]
https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html

![[Pasted image 20210708095812.png]]


#### 上传到服务器任意位置，然后解压
```bash
sudo tar -zxv -f jdk-8u291-linux-x64.tar.gz -C /usr/local/
```


#### 然后配置服务器环境变量
export JAVA_HOME=/usr/local/jdk1.8.0_291/
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin
