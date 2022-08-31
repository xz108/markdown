```
bind 127.0.0.1 #注释掉这部分，使redis可以外部访问
daemonize no#用守护线程的方式启动
requirepass 你的密码#给redis设置密码
appendonly yes#redis持久化　　默认是no
tcp-keepalive 300 #防止出现远程主机强迫关闭了一个现有的连接的错误 默认是300

   wget http://download.redis.io/redis-stable/redis.conf
```
   
   五、创建本地与docker映射的目录，即本地存放的位置
   ```
  docker run --name redis_me -p 6379:6379 \
  -v /data/redis/data:/data \
  -v /data/redis/redis.conf:/etc/redis/redis.conf \
  -d redis redis-server /etc/redis/redis.conf
 
   ```
   docker run --restart=always --log-opt max-size=100m --log-opt max-file=2 -p 6379:6379 --name myredis -v /home/redis/myredis/myredis.conf:/etc/redis/redis.conf -v /home/redis/myredis/data:/data -d redis redis-server /etc/redis/redis.conf  --appendonly yes

   ````
docker run -d --name redis-master1  --privileged=true -p 6379:6379 -v /data/redis:/etc/redis -v /data/redis/data:/data redis /usr/local/bin/redis-server /etc/redis/redis.conf
   
   docker run -d --name redis-slave1  --privileged=true -p 6380:6380 -v /data/redis:/etc/redis -v /data/redis/data:/data redis /usr/local/bin/redis-server /etc/redis/redis-slave1.conf

   docker run -d --name redis-slave2  --privileged=true -p 6381:6381 -v /data/redis:/etc/redis -v /data/redis/data:/data redis /usr/local/bin/redis-server /etc/redis/redis-slave2.conf

    docker inspect redis-6379 | grep IPAddress
    lsof -i
   ````
   # 删除更改配置之后的redis容器
   ```
   docker stop redis-master1
   docker rm redis-master1

      docker stop redis-slave1
   docker rm redis-slave1

      docker stop redis-slave2
   docker rm redis-slave2
```
```
port 20001
 
dir "/data"
 
logfile "sentinel-20001.log"
 
sentinel monitor master-1 1.15.226.69 6379 2
 
sentinel down-after-milliseconds mymaster 10000
 
sentinel failover-timeout mymaster 60000
 
sentinel auth-pass master-1 masterpass
```

```
docker run -p 20001:20001  --name sentinel-20001 -v /data/redis/sentinel:/etc/redis -v /data/redis/sentinel/data:/data -d redis /usr/local/bin/redis-sentinel /etc/redis/sentinel-20001.conf

docker run -p 20002:20002  --name sentinel-20002 -v /data/redis/sentinel:/etc/redis -v /data/redis/sentinel/data:/data -d redis /usr/local/bin/redis-sentinel /etc/redis/sentinel-20002.conf

docker run -p 20003:20003  --name sentinel-20003 -v /data/redis/sentinel:/etc/redis -v /data/redis/sentinel/data:/data -d redis /usr/local/bin/redis-sentinel /etc/redis/sentinel-20003.conf
```