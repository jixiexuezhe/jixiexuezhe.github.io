## widows 

### netstat -ano |findstr "端口号"

### tasklist /fi "imagename eq nginx.exe"
### taskkill /f /t /im "进程id或者进程名称"


## linux 

netstat -ntulp  | grep "端口号"
kill -9 "端口号"

###  查看防火墙     firewall-cmd --state
###  停止防火墙     systemctl stop firewalld.service
###  禁止开机启动   systemctl disable firewalld.service
###  关闭SELINUX
vi /etc/selinux/config
将SELINUX=enforcing改为SELINUX=disabled

## 安装telnet
### 查看是否安装 rpm -qa | grep telnet
### 然后检查yum列表里面有什么
### [root~]# yum list | grep telnet
### telnet-server.x86_64                       1:0.17-48.el6                 @base  
### telnet.x86_64                              1:0.17-48.el6                 base 

### yum install -y telnet-server.x86_64
### yum install -y telnet.x86_64


## centos7 时间设置 （查看 timedatectl ）

### 终端输入命令：tzselect

### 根据提示选择：
### 5 --> 9-->1-->1-->ok

### cat /etc/sysconfig/clock ZONE=Asia/Shanghai (新机器可忽略)
### rm /etc/localtime (新机器可忽略)
### ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

### 局域网时间同步 ： https://www.cnblogs.com/onlookers/p/4308383.html

## 华为云修改hostname
vi /etc/hostname 然后reboot
参考这个地址貌似没反应：https://segmentfault.com/a/1190000005631361
