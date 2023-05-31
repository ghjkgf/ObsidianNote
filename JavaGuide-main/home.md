---
icon: creative
title: JavaGuide（Java学习&&面试指南）
---

## 项目相关

* [项目介绍](intro.md)
* [贡献指南](contribution-guideline.md)
* [常见问题](faq.md)
* [项目代办](todo.md)

## Java

### 基础

**知识点/面试题总结** : (必看:+1: )：

- [Java 基础常见知识点&面试题总结(上)](java-basic-questions-01.md)
- [Java 基础常见知识点&面试题总结(中)](java-basic-questions-02.md)
- [Java 基础常见知识点&面试题总结(下)](java-basic-questions-03.md)

**重要知识点详解** ：

- [为什么 Java 中只有值传递？](why-there-only-value-passing-in-java.md)
- [Java 序列化详解](serialization.md)
- [泛型&通配符详解](generics-and-wildcards.md)
- [Java 反射机制详解](reflection.md)
- [Java 代理模式详解](proxy.md)
- [BigDecimal 详解](bigdecimal.md)
- [Java 魔法类 Unsafe 详解](unsafe.md)
- [Java SPI 机制详解](spi.md)
- [Java 语法糖详解](syntactic-sugar.md)

### 集合

**知识点/面试题总结** ：

- [Java 集合常见知识点&面试题总结(上)](java-collection-questions-01.md) (必看 :+1:)
- [Java 集合常见知识点&面试题总结(下)](java-collection-questions-02.md) (必看 :+1:)
- [Java 容器使用注意事项总结](java-collection-precautions-for-use.md)

**源码分析** ：

* [ArrayList 源码+扩容机制分析](arraylist-source-code.md)
* [HashMap(JDK1.8)源码+底层数据结构分析](hashmap-source-code.md)
* [ConcurrentHashMap 源码+底层数据结构分析](concurrent-hash-map-source-code.md)

### IO

* [IO 基础知识总结](io-basis.md)
* [IO 设计模式总结](io-design-patterns.md)
* [IO 模型详解](io-model.md)

### 并发

**知识点/面试题总结** : (必看 :+1:)

- [Java 并发常见知识点&面试题总结（上）](java-concurrent-questions-01.md)
- [Java 并发常见知识点&面试题总结（中）](java-concurrent-questions-02.md)
- [Java 并发常见知识点&面试题总结（下）](java-concurrent-questions-03.md)

**重要知识点详解** ：

- [JMM（Java 内存模型）详解](JavaGuide-main/docs/java/concurrent/jmm.md)
- **线程池** ：[Java 线程池详解](java-thread-pool-summary.md)、[Java 线程池最佳实践](java-thread-pool-best-practices.md)
- [ThreadLocal 详解](threadlocal.md)
- [Java 并发容器总结](java-concurrent-collections.md)
- [Atomic 原子类总结](atomic-classes.md)
- [AQS 详解](aqs.md)
- [CompletableFuture入门](completablefuture-intro.md)

### JVM (必看 :+1:)

JVM 这部分内容主要参考 [JVM 虚拟机规范-Java8 ](https://docs.oracle.com/javase/specs/jvms/se8/html/index.html) 和周志明老师的[《深入理解Java虚拟机（第3版）》](https://book.douban.com/subject/34907497/) （强烈建议阅读多遍！）。

- **[Java 内存区域](memory-area.md)**
- **[JVM 垃圾回收](jvm-garbage-collection.md)**
- [类文件结构](class-file-structure.md)
- **[类加载过程](class-loading-process.md)**
- [类加载器](classloader.md)
- [【待完成】最重要的 JVM 参数总结（翻译完善了一半）](jvm-parameters-intro.md)
- [【加餐】大白话带你认识 JVM](jvm-intro.md)
- [JDK 监控和故障处理工具](jdk-monitoring-and-troubleshooting-tools.md)

### 新特性

- **Java 8** ：[Java 8 新特性总结（翻译）](java8-tutorial-translate.md)、[Java8常用新特性总结](java8-common-new-features.md)
- [Java 9 新特性概览](java9.md)
- [Java 10 新特性概览](java10.md)
- [Java 11 新特性概览](java11.md)
- [Java 12~13 新特性概览](java12-13.md)
- [Java 14 新特性概览](java14.md)
- [Java 15 新特性概览](java15.md)
- [Java 16 新特性概览](java16.md)
- [Java 17 新特性概览](java17.md)
- [Java 18 新特性概览](java18.md)
- [Java 19 新特性概览](java19.md)

## 计算机基础

### 操作系统

- [操作系统常见问题总结！](operating-system-basic-questions-01.md)
- [后端程序员必备的 Linux 基础知识总结](linux-intro.md)
- [Shell 编程基础知识总结](shell-intro.md)

### 网络

**知识点/面试题总结** ：

- [计算机网络常见知识点&面试题总结](other-network-questions.md)
- [谢希仁老师的《计算机网络》内容总结（补充）](computer-network-xiexiren-summary.md)

**重要知识点详解** ：

- [OSI 和 TCP/IP 网络分层模型详解（基础）](osi&tcp-ip-model.md)
- [应用层常见协议总结（应用层）](application-layer-protocol.md)
- [HTTP vs HTTPS（应用层）](http&https.md)
- [HTTP 1.0 vs HTTP 1.1（应用层）](http1.0&http1.1.md)
- [HTTP 常见状态码（应用层）](http-status-codes.md)
- [TCP 三次握手和四次挥手（传输层）](tcp-connection-and-disconnection.md)
- [TCP 传输可靠性保障（传输层）](tcp-reliability-guarantee.md)
- [ARP 协议详解(网络层)](arp.md)

### 数据结构

**图解数据结构：**

- [线性数据结构 :数组、链表、栈、队列](linear-data-structure.md)
- [图](graph.md)
- [堆](heap.md)
- [树](tree.md) ：重点关注[红黑树](red-black-tree.md)、B-，B+，B*树、LSM树

其他常用数据结构 ：

- [布隆过滤器](bloom-filter.md)

### 算法

算法这部分内容非常重要，如果你不知道如何学习算法的话，可以看下我写的：

* [算法学习书籍+资源推荐](https://www.zhihu.com/question/323359308/answer/1545320858) 。
* [如何刷Leetcode?](https://www.zhihu.com/question/31092580/answer/1534887374) 

**常见算法问题总结** ：

* [几道常见的字符串算法题总结 ](string-algorithm-problems.md)
* [几道常见的链表算法题总结 ](linkedlist-algorithm-problems.md)
* [剑指 offer 部分编程题](the-sword-refers-to-offer.md)
* [十大经典排序算法](10-classical-sorting-algorithms.md)

另外，[GeeksforGeeks]( https://www.geeksforgeeks.org/fundamentals-of-algorithms/) 这个网站总结了常见的算法 ，比较全面系统。

## 数据库

### 基础

- [数据库基础知识总结](basis.md)
- [字符集详解](character-set.md)

### MySQL

**知识点/面试题总结：**

- **[MySQL知识点总结](mysql-questions-01.md)** (必看 :+1:)
- [MySQL 高性能优化规范建议总结](mysql-high-performance-optimization-specification-recommendations.md)

**重要知识点：**

- [MySQL数据库索引总结](mysql-index.md)
- [事务隔离级别(图文详解)](transaction-isolation-level.md)
- [MySQL三大日志(binlog、redo log和undo log)详解](mysql-logs.md)
- [InnoDB存储引擎对MVCC的实现](innodb-implementation-of-mvcc.md)
- [SQL语句在MySQL中的执行过程](how-sql-executed-in-mysql.md)
- [关于数据库中如何存储时间的一点思考](some-thoughts-on-database-storage-time.md)
- [MySQL中的隐式转换造成的索引失效](index-invalidation-caused-by-implicit-conversion.md)

### Redis

**知识点/面试题总结** : (必看:+1: )：

- [Redis 常见问题总结(上)](redis-questions-01.md)
- [Redis 常见问题总结(下)](redis-questions-02.md)

**重要知识点：**

- [3种常用的缓存读写策略详解](3-commonly-used-cache-read-and-write-strategies.md)
- [Redis 5 种基本数据结构详解](redis-data-structures-01.md)
- [Redis 3 种特殊数据结构详解](redis-data-structures-02.md)
- [Redis 内存碎片详解](redis-memory-fragmentation.md)
- [Redis 集群详解](redis-cluster.md)

## 搜索引擎

用于提高搜索效率，功能和浏览器搜索引擎类似。比较常见的搜索引擎是 Elasticsearch（推荐） 和 Solr。

## 开发工具

### Docker

* [Docker 基本概念解读](docker-intro.md)
* [Docker从入门到上手干事](docker-in-action.md)

### Git

* [Git 入门](git-intro.md)
* [Github 小技巧](github-tips.md)

## 系统设计

- [系统设计常见面试题总结](system-design-questions.md)
- [设计模式常见面试题总结](design-pattern.md)

### 基础

- [RestFul API 简明教程](RESTfulAPI.md)
- [Java 编码命名之道](naming.md) 
- [代码重构指南](refactoring.md)
- [单元测试指南](unit-test.md)

### 常用框架

#### Spring/SpringBoot (必看 :+1:)

**知识点/面试题总结** :

- [Spring 常见知识点&面试题总结](spring-knowledge-and-questions-summary.md)
- [SpringBoot 常见知识点&面试题总结](springboot-knowledge-and-questions-summary.md)
- [Spring/Spring Boot 常用注解总结](spring-common-annotations.md)
- [SpringBoot 入门指南](https://github.com/Snailclimb/springboot-guide)

**重要知识点详解** ：

- [Spring 事务详解](spring-transaction.md)
- [Spring 中的设计模式详解](spring-design-patterns-summary.md)
- [SpringBoot 自动装配原理详解](spring-boot-auto-assembly-principles.md)

#### MyBatis

[MyBatis 常见面试题总结](mybatis-interview.md)

### 安全

#### 认证授权

- [认证授权基础概念详解](basis-of-authority-certification.md)
- [JWT 基础概念详解](jwt-intro.md)
- [JWT 优缺点分析以及常见问题解决方案](advantages&disadvantages-of-jwt.md)
- [SSO 单点登录详解](sso-intro.md)
- [权限系统设计详解](design-of-authority-system.md)

#### 数据脱敏

数据脱敏说的就是我们根据特定的规则对敏感信息数据进行变形，比如我们把手机号、身份证号某些位数使用 * 来代替。

#### 敏感词过滤

[敏感词过滤方案总结](sentive-words-filter.md)

### 定时任务

[Java 定时任务详解](schedule-task.md)

### Web 实时消息推送

[Web 实时消息推送详解](web-real-time-message-push.md)

## 分布式

### 理论&算法&协议

- [CAP 理论和 BASE 理论解读](cap&base-theorem.md)
- [Paxos 算法解读](paxos-algorithm.md)
- [Raft 算法解读](raft-algorithm.md)

### API 网关

[API 网关详解](api-gateway.md)

### 分布式 ID

[分布式 ID 详解](distributed-id.md)

### 分布式锁

[分布式锁详解](distributed-lock.md)

### 分布式事务

[分布式事务详解](distributed-transaction.md)

### 分布式配置中心

[分布式配置中心详解](distributed-configuration-center.md)

### RPC

* [RPC 基础常见知识点&面试题总结](rpc-intro.md)
* [Dubbo 常见知识点&面试题总结](dubbo.md)

### ZooKeeper

> 前两篇文章可能有内容重合部分，推荐都看一遍。

- [ZooKeeper 相关概念总结(入门)](zookeeper-intro.md)
- [ZooKeeper 相关概念总结(进阶)](zookeeper-plus.md)
- [ZooKeeper 实战](zookeeper-in-action.md)

## 高性能

### 读写分离&分库分表

[读写分离&分库分表详解](read-and-write-separation-and-library-subtable.md)

### 负载均衡

[负载均衡详解](load-balancing.md)

### SQL 优化

[常见 SQL 优化手段总结](sql-optimization.md)

### CDN

[CDN（内容分发网络）详解](cdn.md)

### 消息队列

消息队列在分布式系统中主要是为了解耦和削峰。相关阅读： [消息队列常见问题总结](message-queue.md)。

- **RabbitMQ** : [RabbitMQ 基础知识总结](rabbitmq-intro.md)、[RabbitMQ 常见面试题](rabbitmq-questions.md)
- **RocketMQ** : [RocketMQ 基础知识总结](rocketmq-intro.md)、[RocketMQ 常见面试题总结](rocketmq-questions.md)
- **Kafka** ：[Kafka 常见问题总结](kafka-questions-01.md)

## 高可用

[高可用系统设计指南](high-availability-system-design.md)

### 冗余设计

[冗余设计详解](redundancy.md)

### 限流

[服务限流详解](limit-request.md)

### 降级&熔断

[降级&熔断详解](fallback&circuit-breaker.md)

### 超时&重试

[超时&重试详解](timeout-and-retry.md)

### 集群

相同的服务部署多份，避免单点故障。

### 灾备设计和异地多活

**灾备**  = 容灾+备份。

* **备份** ： 将系统所产生的的所有重要数据多备份几份。
* **容灾** ： 在异地建立两个完全相同的系统。当某个地方的系统突然挂掉，整个应用系统可以切换到另一个，这样系统就可以正常提供服务了。

**异地多活** 描述的是将服务部署在异地并且服务同时对外提供服务。和传统的灾备设计的最主要区别在于“多活”，即所有站点都是同时在对外提供服务的。异地多活是为了应对突发状况比如火灾、地震等自然或者人为灾害。


