 ### 标准格式
```bash
sudo java -jar demo.jar --spring.config.location=路径（application.yml）
```


#### jar 包启动时指定配置文件 application.yml

```bash
sudo nohup java -jar -Dserver.port=8080 wx-member-card-0.0.1-SNAPSHOT.war --spring.config.location=file:./application-prod.yml &
```

```bash
nohup java -jar vTest.jar  --spring.config.location=/opt/vTest-conf/application.yml >  /opt/vTest-conf/nohup.out 2>&1 &
```

如果不喜欢将 application.properties  作为配置文件名，你也可以通过指定 spring.config.name  环境属性来切换其他的名称

也可以使用 spring.config.location  环境属性引用一个明确的路径（目录位置或文件路径）

#### 指定配置文件：
```bash
--spring.config.location=/opt/vpaas-conf/application.yml
```

将所有的调试信息输入到：/opt/vpaas-conf/nohup.out

------------------

SYNC
nohup java -jar kkswap2-sync.jar --spring.config.location=./application.yml 2>&1 &

API
nohup java -jar kkswap2-api.jar --spring.config.location=./application.yml 2>&1 &