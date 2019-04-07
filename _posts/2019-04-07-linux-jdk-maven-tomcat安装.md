jdk 下载  https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

安装 ：进入根目录下的etc文件夹，打开profile文件进行编辑  
vi /etc/profile
在末尾加入代码
#set java environment
export JAVA_HOME=/usr/java/jdk1.8.0_202
export JRE_HOME=/usr/java/jdk1.8.0_202/jre
export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$JAVA_HOME:$PATH

完成jdk环境变量的配置后保存并在命令行界面执行  source /etc/profile

maven 安装
tar vxf apache-maven-3.5.4-bin.tar.gz

在/etc/profile中添加以下几行

MAVEN_HOME=/opt/apache-maven-3.5.4
export MAVEN_HOME
export PATH=${PATH}:${MAVEN_HOME}/bin

完成后执行source /etc/profile使环境变量生效。

安装tomcat  http://tomcat.apache.org/download-80.cgi#8.0.46
tar -zxvf aapache-tomcat-8.5.39.tar.gz
cd  /opt/apache-tomcat-8.5.39/bin
./startup.sh
