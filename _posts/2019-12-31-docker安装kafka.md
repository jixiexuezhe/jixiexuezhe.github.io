
docker pull zookeeper:3.5.6
docker pull wurstmeister/kafka
docker run -d --name zookeeper  -p 2181:2181 zookeeper:3.5.6

docker run -d --name kafka -p 9092:9092 \
--link zookeeper:zookeeper \
--env KAFKA_BROKER_ID=1 \
--env HOST_IP=39.107.51.65 \
--env KAFKA_ZOOKEEPER_CONNECT=zookeeper:2181 \
--env KAFKA_ADVERTISED_HOST_NAME=39.107.51.65 \
--env KAFKA_ADVERTISED_PORT=9092 \
-t wurstmeister/kafka

创建topic
bin/kafka-topics.sh --create \
--zookeeper 39.107.51.65:2181 \
--topic test1 \
--partitions 3 \
--replication-factor 1

查看topic
bin/kafka-topics.sh --describe --zookeeper 39.107.51.65:2181 --topic test1

启动生产者
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test1

启动消费者
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test1

参考来源： https://blog.csdn.net/wyq232417/article/details/88753417
