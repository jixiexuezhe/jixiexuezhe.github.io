
## 1. docker pull mysql:8.0.18
## 2. mkdir -p /opt/docker-mysql/conf.d
## 3. cd /opt/docker-mysql/conf.d 然后  vi my.cnf

#########################################################  
[mysqld]
# 表名不区分大小写
lower_case_table_names=1 
#server-id=1
datadir=/var/lib/mysql
#socket=/var/lib/mysql/mysqlx.sock
#symbolic-links=0
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES 
[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
#########################################################  

## 4.  mkdir -p /opt/docker-mysql/var/lib/mysql
## 5. 
 docker run --name mysql \
    --restart=always \
    -p 3306:3306 \
    -v /opt/docker-mysql/conf.d:/etc/mysql/conf.d \
    -v /opt/docker-mysql/var/lib/mysql:/var/lib/mysql \
    -e MYSQL_ROOT_PASSWORD=123456 \
    -d mysql:8.0.18
  
## 6.   docker exec -it mysql bash
  docker logs -f mysql
    
    安装参考 ： https://www.jianshu.com/p/d6febf6f95e0
## 7. 远程无法登录解决办法

	create user 'alex'@'%' identified by 'alex';
	
	GRANT ALL PRIVILEGES ON *.* TO 'alex'@'%';
	
	ALTER USER 'alex'@'%' IDENTIFIED WITH mysql_native_password BY 'alex';

参考链接： https://www.cnblogs.com/php-linux/p/11561300.html
