### 1. 先在主机安装docker ，jdk，maven，git
### 2. docker 安装Jenkins 参考地址： https://www.jianshu.com/p/9792c892cf54
###  jendins启动命令：
docker run \
  --name jenkins_docker \
  -p 8091:8080 \
  -u root \
  -v /home/jenkins/jenkins-data:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /opt/apache-maven-3.5.4:/usr/local/maven3.5 \
  -v /usr/java/jdk1.8.0_202:/usr/local/jdk1.8 \
  -d \
  jenkins/jenkins:lts 
  
###  秘钥生成
####  docker exec -it jenkins /bin/bash
####  ssh-keygen -t rsa -C "123@qq.com"
  
###  3. 配置Jenkins 参考： https://www.jianshu.com/p/a7d7df97fe4b


git 安装：  https://blog.csdn.net/xwj1992930/article/details/96428998
            https://www.jianshu.com/p/be56c8410396

配置远程服务器参考： https://blog.csdn.net/weixin_30457551/article/details/99329907
和： https://blog.csdn.net/JqueryTomcat/article/details/88966992


远程服务器 exec commend不生效解决 办法参考
https://blog.csdn.net/lixuegen/article/details/90033599

执行 nohup报错： nohup: failed to run command ‘java’: No such file or directory
可以使用如下命令：
vi .bashrc    （添加Java 环境变量即可）
source .bashrc 




执行 nohup后一直转圈圈参考：https://blog.csdn.net/bpqdwo/article/details/88249325

pid=`ps -ef | grep eureka-1.0.1-SNAPSHOT.jar | grep -v grep | awk '{print $2}'`
if [ -n "$pid" ]
then
   kill -9 $pid
fi
chmod +777 /root/jenkinstest/eureka-1.0.1-SNAPSHOT.jar
OLD_BUILD_ID=$BUILD_ID
echo $OLD_BUILD_ID
export BUILD_ID=dontKillMe
nohup  java  -jar /root/jenkinstest/eureka-1.0.1-SNAPSHOT.jar  > /root/jenkinstest/nohup.out  & 2>&1 &
export BUILD_ID=$OLD_BUILD_ID
echo $BUILD_ID
sleep 20s
cat  /root/jenkinstest/nohup.out 
echo "服务器查看日志路径 /root/jenkinstest/nohup.out"



### 添加新用户 并管理 权限 ： https://blog.csdn.net/pansaky/article/details/80746736
