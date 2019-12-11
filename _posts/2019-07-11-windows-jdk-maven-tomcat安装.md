jdk安装及环境变量配置:

下载链接: https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html  
下载windows版本 jdk-8u211-windows-x64.exe  
双击安装,然后配置环境变量:  
1. JAVA_HOME   变量值填写jdk的安装目录（bin上一层目录)  
2.在Path下加入   %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;  
3.在CLASSPATH 下加入  .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar  
cmd 输入 java -version  

maven安装及环境变量配置  

下载链接:  http://maven.apache.org/download.cgi  
下载 apache-maven-3.6.1-bin.zip  直接解压  
1. MAVEN_HOME   变量值填写maven的安装目录（bin上一层目录)  
2. Path中添加 %MAVEN_HOME%\bin;  
3. cmd 输入 mvn -version  

Tomcat 安装及环境变量配置  
下载链接: https://tomcat.apache.org/download-80.cgi  
下载window版本  apache-tomcat-8.5.43.zip  
1.  CATALINA_BASE  变量值填写Tomcat的安装目录  
2.  CATALINA_HOME  变量值填写Tomcat的安装目录  
3. Path 下加入  %CATALINA_HOME%\lib;%CATALINA_HOME%\bin;  
4. cmd 输入 startup   启动后浏览器输入 localhost:8080验证是否成功.  
