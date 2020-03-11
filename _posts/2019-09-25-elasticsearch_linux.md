安装参考 https://www.cnblogs.com/jingping/p/9448099.html  

## 1 创建 elasticsearch 用户组
[root@localhost ~]# groupadd elasticsearch  

## 2 创建用户 es 并设置密码为es
[root@localhost ~]# useradd es  
[root@localhost ~]# passwd es  

## 3 用户es 添加到 elasticsearch 用户组  
[root@localhost ~]# usermod -G elasticsearch es  

## 4 设置sudo权限
[root@localhost ~]# visudo  

在root ALL=(ALL) ALL 一行下面  
添加es用户 如下:  
es ALL=(ALL) ALL  
 
添加成功保存后切换到es用户操作  
[root@localhost ~]# su es  

下载镜像地址 https://thans.cn/mirror/elasticsearch.html  

[es@localhost src]$ wget https://elasticsearch.thans.cn/downloads/elasticsearch/elasticsearch-5.5.1.tar.gz  
[es@localhost src]$ tar -xvf elasticsearch-5.5.1.tar.gz  
[es@localhost src]$ sudo mv elasticsearch-5.5.1 /usr/local  
[es@localhost local]$ sudo chown -R es:elasticsearch elasticsearch-5.5.1  

## 5  elasticsearch.yml 修改  
[es@localhost elasticsearch-6.3.2]$ vim config/elasticsearch.yml  

cluster.name: my-application  
node.name: node-1  
network.host: 0.0.0.0   
http.port: 9200  

 切换回root 用户 执行  

vim /etc/sysctl.conf  
在文件最后面添加内容:  
vm.max_map_count=262144  

保存退出后,使用sysctl -p 刷新生效  
vim /etc/security/limits.conf  

* hard nofile 65536  
* soft nofile 65536  
 
* soft nproc 2048  
* hard nproc 4096  

vi /etc/profile 将 ulimit -n 65535 行注释掉，退出重新进入当前用户，再使用 ulimit -Hn 查看当前值，已经是131072了，设置成功！  
退出重新登录  
bin/elasticsearch (后台运行  bin/elasticsearch -d )  
jps 查看进程  

bash-4.2$ curl http://172.16.3.20:9200?pretty  
{
  "name" : "node-1",  
  "cluster_name" : "elasticsearch",  
  "cluster_uuid" : "t20t7D1FRdeMGzwbFDGObg",  
  "version" : {  
    "number" : "5.5.1",  
    "build_hash" : "19c13d0",  
    "build_date" : "2017-07-18T20:44:24.823Z",  
    "build_snapshot" : false,  
    "lucene_version" : "6.6.0"  
  },  
  "tagline" : "You Know, for Search"  
}  

----------------------------------------------------------------------  
elasticsearch6.4 memory locking requested for elasticsearch process but memory is not locked 终极解决
https://www.cnblogs.com/gaoyuechen/p/9842349.html
