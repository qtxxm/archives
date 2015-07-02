# centos tomcat 开机启动

编辑tomcat开机启动脚本
```shell
vi /etc/init.d/tomcat
```

脚本内容如下
```shell
#!/bin/bash  
# description: Tomcat Start Stop Restart  
# processname: tomcat  
# chkconfig: 234 20 80  
CATALINA_HOME=/usr/share/apache-tomcat-7.0.29  
  
case $1 in  
start)  
sh $CATALINA_HOME/bin/startup.sh  
;;   
stop)     
sh $CATALINA_HOME/bin/shutdown.sh  
;;   
restart)  
sh $CATALINA_HOME/bin/shutdown.sh  
sh $CATALINA_HOME/bin/startup.sh  
;;   
esac      
exit 0  
```

加入开机启动配置
```shell
chmod 755 /etc/init.d/tomcat 
chkconfig --add tomcat
chkconfig --level 234 tomcat on
```

验证
```shell
chkconfig --list tomcat 
```