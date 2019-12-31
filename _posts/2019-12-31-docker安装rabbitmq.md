## 1. rabbitmq 安装
docker pull rabbitmq:3.8.2-management

docker run -d -p 5672:5672 -p 15672:15672 --name rabbitmq rabbitmq:3.8.2-management

http://39.107.51.65:15672 guest guest

## 2. acitvemq 安装

docker pull webcenter/activemq

docker run --name activemq -p 61616:61616 -p 8161:8161  -e ACTIVEMQ_ADMIN_LOGIN=admin -e ACTIVEMQ_ADMIN_PASSWORD=123456 --restart=always -d webcenter/activemq

http://39.107.51.65:8161 admin 123456

参考来源：https://blog.csdn.net/xu12387/article/details/87910867
