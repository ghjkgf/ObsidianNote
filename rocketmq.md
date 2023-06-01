## 安装

### docker 部署
新建文件夹 C:/java/dockerRocketMQ
新建文件 C:/java/dockerRocketMQ/conf/broker.conf
```
brokerClusterName = DefaultCluster
brokerName = broker-a
brokerId = 0
deleteWhen = 04
fileReservedTime = 48
brokerRole = ASYNC_MASTER
flushDiskType = ASYNC_FLUSH
brokerIP1 = 192.168.1.165   # ip 千万别用127.0.0.1啊
```

docker run -d -p 9876:9876 -v C:/java/dockerRocketMQ/data/namesrv/logs:/root/logs -v C:/java/dockerRocketMQ/data/namesrv/store:/root/store --name rmqnamesrv -e "MAX_POSSIBLE_HEAP=100000000" apacherocketmq/rocketmq sh mqnamesrv

docker run -d -p 10911:10911 -p 10909:10909 -v  C:/java/dockerRocketMQ/data/broker/logs:/root/logs -v  C:/java/dockerRocketMQ/rocketmq/data/broker/store:/root/store -v  C:/java/dockerRocketMQ/conf/broker.conf:/opt/rocketmq/conf/broker.conf --name rmqbroker --link rmqnamesrv:namesrv -e "NAMESRV_ADDR=namesrv:9876" -e "MAX_POSSIBLE_HEAP=200000000" apacherocketmq/rocketmq sh mqbroker -c /opt/rocketmq/conf/broker.conf

 docker run -e "JAVA_OPTS=-Drocketmq.config.namesrvAddr=192.168.1.165:9876 
 -Drocketmq.config.isVIPChannel=false" -p 8088:8080 -t apacherocketmq/rocketmq-dashboard

### docker-compose方式
还不会

## 使用
在broker里
	mqadmin updatetopic -n 192.168.1.165:9876 -t TestTopic -c DefaultCluster