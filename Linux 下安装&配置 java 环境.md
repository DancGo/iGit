#### 首先下载 java sdk 包
[当前流程为 jdk8]
https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html

![[photo/Pasted image 20210708095812.png]]


#### 上传到服务器任意位置，然后解压
```bash
sudo tar -zxv -f jdk-8u291-linux-x64.tar.gz -C /usr/local/
```


#### 然后配置服务器环境变量
```bash
export JAVA_HOME=/usr/local/jdk1.8.0_291/
```
```bash
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```
```bash
export PATH=$PATH:$JAVA_HOME/bin
```



#### 编辑环境变量文件
```bash
sudo vim /etc/profile
```
 在文件末尾添加同上内容后保存退出
```bash
export JAVA_HOME=/usr/local/jdk1.8.0_291/
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin
```


#### 最后验证 java sdk 状态
```bash
java –version
```
![[photo/Pasted image 20210708100138.png]]
