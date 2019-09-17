## widows 

netstat -ano |findstr "端口号"
taskkill /f /t /im "进程id或者进程名称"


## linux 

netstat -ntulp "端口号"

kill -9 "端口号"


查看防火墙     firewall-cmd --state
停止防火墙     systemctl stop firewalld.service
禁止开机启动   systemctl disable firewalld.service
关闭SELINUX
vi /etc/selinux/config
将SELINUX=enforcing改为SELINUX=disabled
