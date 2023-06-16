# KettlePack - docker版说明



- [官方仓库地址](https://hub.docker.com/r/congjing/kettlepack)

```
docker pull congjing/kettlepack:latest
```

- 阿里云仓库地址

```
docker pull registry.cn-hangzhou.aliyuncs.com/congjing/kettlepack:latest
```





## 运行方式



### 运行方式1 ： 单独运行

此方式使用本地mysql数据库

建库语句：

```mysql
CREATE DATABASE `kettle-pack` CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```

创建kettle-pack容器：

```shell
docker run -d \
--restart=always \
-p 9089:9089 \
-e JDBC_HOST=192.168.xxx.xxx \
-e JDBC_PORT=3306 \
-e JDBC_USERNAME=root \
-e JDBC_PASSWORD=password \
--name kettle-pack \
congjing/kettlepack:latest
```



### 运行方式2 ： 配合mysql运行



#### 创建mysql容器

```shell
docker run -d \
--restart=always \
-p 13306:3306 \
-e MYSQL_ROOT_PASSWORD=congjingkeji \
-e MYSQL_DATABASE=kettle-pack \
-e TZ=Asia/Shanghai \
--name kettle-pack-mysql \
mysql:5.7 \
--lower_case_table_names=1 \
--character-set-server=utf8mb4 \
--collation-server=utf8mb4_general_ci
```



#### 创建kettle-pack容器

```shell
docker run -d \
--restart=always \
--link kettle-pack-mysql \
-p 9089:9089 \
--name kettle-pack \
congjing/kettlepack:latest
```



### 运行方式3 ： docker-compose



#### docker-compose.yml

```yaml
version: '3'
services:
  kettle-pack-mysql:
    container_name: kettle-pack-mysql
    restart: always
    image: mysql:5.7
    environment:
      TZ: Asia/Shanghai
      MYSQL_ROOT_PASSWORD: congjingkeji
      MYSQL_DATABASE: kettle-pack
    command:
      --character-set-server=utf8mb4
      --collation-server=utf8mb4_general_ci
      --lower_case_table_names=1
    ports:
       - 13306:3306
  kettle-pack:
    container_name: kettle-pack
    restart: always
    depends_on:
      - kettle-pack-mysql
    image: congjing/kettlepack:latest
    ports:
      - '9089:9089'
    environment:
      JDBC_HOST: kettle-pack-mysql
      JDBC_PORT: 3306
      JDBC_USERNAME: root
      JDBC_PASSWORD: congjingkeji

```

下载地址：http://kettlepack.congjing.net/download/docker-compose.yml



#### 启动

```shell
docker-compose up -d
```




## 其它配置



### 数据库连接参数

指定mysql数据库连接：

| 参数          | 说明            | 默认值       |
| ------------- | --------------- | ------------ |
| JDBC_HOST     | mysql服务器地址 |              |
| JDBC_PORT     | mysql端口号     | 3306         |
| JDBC_USERNAME | mysql用户名     | root         |
| JDBC_PASSWORD | mysql密码       | congjingkeji |

例：

```
docker run -d \
-e JDBC_HOST=192.168.xxx.xxx \
...
congjing/kettlepack:latest
```





### 目录说明 

可将以下路径映射至宿主机

| 路径                       | 说明                                                         |
| -------------------------- | ------------------------------------------------------------ |
| /opt/kettle-pack/plugins   | kettle插件目录，版本：8.3.0.0-371                            |
| /opt/kettle-pack/workspace | 工作空间，用于存放转换和作业文件，【文件管理】使用的就是此目录 |
| /opt/kettle-pack/logs      | 转换和作业的执行日志                                         |

例：

```
docker run -d \
-v /宿主机路径/kettle-pack/plugins:/opt/kettle-pack/plugins \
...
congjing/kettlepack:latest
```



---

QQ沟通群：[491723218](https://jq.qq.com/?_wv=1027&k=UEWIkTbI)