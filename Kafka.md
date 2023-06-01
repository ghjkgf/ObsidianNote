需要有zookeeper
使用docker-compose方式
```yml
version: '2'
services:
  zookeeper:
    image: "zookeeper"
    hostname: "zookeeper.local"
    container_name: "zookeeper"
    #设置网络别名
    networks:
      local:
        aliases:
          - "zookeeper.local"
  kafka:
    image: "wurstmeister/kafka"
    hostname: "kafka.local"
    container_name: "kafka"
    ports:
      - "9092:9092"
    networks:
      local:
        aliases:
          - "kafka.local"
    environment:
      KAFKA_ADVERTISED_HOST_NAME: kafka.local
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
  # 管理节点配的不对,暂时不能用
  kafka-manager:
    image: "sheepkiller/kafka-manager"
    hostname: "kafka-manager.local"
    container_name: "manager"
    networks:
        local:
            aliases:
                - "kafka-manager.local"
    ports:
      - "9000:9000"
#设置网络，名为local
networks:
  local:
    driver: bridge
```

执行 docker-compose up -d 后,自动在desktop端生成一个以yml文件上级路径名为名的container,可以展开看到里面的子项

执行  docker exec -it kafka bash 进入容器
一个窗口建立topic,建立生产者
	kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 8 --topic test
	kafka-console-producer.sh --broker-list localhost:9092 --topic test
另外一个建立消费者
	kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
在生产者窗口>后输入任意内容,在消费者窗口可以看到消费成功
![[Pasted image 20230128165355.png]]

如何将kafka-manager整合进去?
单独启动zookeeper 可以使用manager
compose的方式会报错