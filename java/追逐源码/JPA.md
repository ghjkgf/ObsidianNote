JPA 中能够支持面向对象的高级特性，如类之间的继承、多态和类之间的复杂关系，这样的支持能够让开发者最大限度的使用面向对象的模型设计企业应用，而不需要自行处理这些特性在关系数据库的持久化。

正如最早学习 JDBC 规范，Java 自身并未提供相关的实现，而是 MySQL 提供 MySQL mysql-connector-java 驱动，Oracle 提供 oracle-jdbc 驱动。而实现 JPA 规范的有：
-   Hibernate ORM
-  [[Oracle TopLink]] 
-   Apache OpenJPA

[Spring Data JPA中常用的注解详解](https://blog.csdn.net/qq_35873847/article/details/79738667)

联合主键设置 @IdClass


jpa插入数据注意,当主键自增时,第一条记录id为1(不管传参多少)

spring:
	  jpa:
    show-sql: true # 打印 SQL 。生产环境，建议关闭
    # Hibernate 配置内容，对应 HibernateProperties 类
    hibernate:
      ddl-auto: none
ddl-auto 五个选项:
-   create ：每次加载 hibernate 时都会删除上一次的生成的表，然后根据你的 model 类再重新来生成新表，哪怕两次没有任何改变也要这样执行，这就是导致数据库表数据丢失的一个重要原因。
-   create-drop ：每次加载 hibernate 时根据 model 类生成表，但是 sessionFactory 一关闭，表就自动删除。
-   update ：最常用的属性，第一次加载 hibernate 时根据 model 类会自动建立起表的结构（前提是先建立好数据库），以后加载 hibernate 时根据 model 类自动更新表结构，即使表结构改变了但表中的行仍然存在不会删除以前的行。要注意的是当部署到服务器后，表结构是不会被马上建立起来的，是要等应用第一次运行起来后才会。
-   validate ：每次加载 hibernate 时，验证创建数据库表结构，只会和数据库中的表进行比较，不会创建新表，但是会插入新值。
-   none : 不使用 Hibernate Auto DDL 功能。


findBy用法![[Pasted image 20210612123247.png]]

