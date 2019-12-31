docker pull rabbitmq:3.8.2-management

docker run -d -p 5672:5672 -p 15672:15672 --name rabbitmq rabbitmq:3.8.2-management

http://39.107.51.65:15672 guest guest
