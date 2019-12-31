
docker pull redis
mkdir /opt/docker-redis
cd /opt/docker-redis

官网获取配置文件http://download.redis.io/redis-stable/redis.conf

配置修改：
#bind 127.0.0.1  
protected-mode no  
appendonly yes//持久化  
requirepass yourpassword  


docker run \
-p 6379:6379 \
-v $PWD/data:/data \
-v $PWD/conf/redis.conf:/etc/redis/redis.conf \
--privileged=true \
--name redis \
-d redis redis-server /etc/redis/redis.conf
