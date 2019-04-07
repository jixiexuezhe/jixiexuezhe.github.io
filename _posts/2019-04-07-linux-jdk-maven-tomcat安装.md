jdk 下载  https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

安装 ：进入根目录下的etc文件夹，打开profile文件进行编辑  

vi profile
#set java environment

export JAVA_HOME=/usr/java/jdk/jdk1.8.0_112

export JRE_HOME=/usr/java/jdk/jdk1.8.0_112/jre

export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH

export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$JAVA_HOME:$PATH
