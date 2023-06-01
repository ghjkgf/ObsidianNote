## docker desktop
使用docker desktop 运行redis 客户端
可以同时开多个窗口
docker exec -it redisA redis-cli

### 直接用本地客户端连接docker里的服务

打开本地redis-cli 文件夹,cmd,输入 -p 6380 即可   (访问远程加 -h ip 即可)  或者 加到环境变量里

容器互通,网桥,巴拉巴拉的
https://blog.csdn.net/qq_44345263/article/details/123327509#:~:text=docker%20desktop%E5%AE%89%E8%A3%85redis%201%201.%E6%8B%89%E5%8F%96redis%E9%95%9C%E5%83%8F%20docker%20hub%E7%9B%B4%E8%BE%BE%20docker%20pull,%E6%98%A0%E5%B0%84%E5%88%B0%E5%AE%BF%E4%B8%BB16379%E7%AB%AF%E5%8F%A3%20...%204%204.%E6%9F%A5%E7%9C%8B%E5%AE%B9%E5%99%A8%E5%B7%B2%E7%BB%8F%E5%9C%A8%E8%BF%90%E8%A1%8C%E4%B8%AD%20%E4%BD%BF%E7%94%A8%20QuickRedis%E5%AE%A2%E6%88%B7%E7%AB%AF%20%E6%B5%8B%E8%AF%95%E9%93%BE%E6%8E%A5%20

功能 | 命令
--- | ---
订阅 | subscribe channelName1 channelName2
发布 | publish channelName message
退订 | unsubscribe 
按模式订阅 | psubscribe
按模式退订 | punsubscribe
查看订阅与发布系统状态 | pubsub + 参数

这个返回值是啥
127.0.0.1:6379> PUBLISH runoobChat2 "why return 0"
(integer) 0
127.0.0.1:6379> publish runoobChat "0000"
(integer) 2
127.0.0.1:6379> publish runoobChat "0000"
(integer) 3
127.0.0.1:6379> publish runoobChat2 "0000"
(integer) 0

java 实现的redis命令
https://try.redis.io
http://doc.redisfans.com

| 类名            | 方法          | 命令     |
| --------------- | ------------- | -------- |
| ValueOperations | set           | set      |
|                 | get           | get      |
|                 | multiSet      | mset     |
|                 | multiGet      | mget     |
|                 | getAndDelete  | getdel   |
|                 | getAndExpire  | getex    |
|                 | getAndPersist | getex    |
|                 | getAndSet     | getset   |
|                 | increment     | incr     |
|                 | decrement     | decr     |
|                 | append        | append   |
|                 | size          | strlen   |
|                 | setBit        | setbit   |
|                 | getBit        | getbit   |
|                 | bitField      | bitfield |
|                 |               | getrange |
|                 |               | setrange |
|                 |               | setex    |
|                 |               | setnx    |
|                 |               | msetnx   |
|                 |               | incrby   |
|                 |               | decrby   |
|                 |               | incrbyfloat         |
查看版本
	redis-server-v
	在redis-cli命令窗口里 info
版本号第二个数字是偶数,代表稳定版

查看 linux 位数
getconf LONG_BIT
先具备gcc编译环境
第三方软件一般放在/opt下
安装在/usr/local/bin下,类似于 C:\ProgramFIles

vim 搜索 使用 / + 单词即可
set nu 显示行号
修改 redis.conf
daemonize yes 后台运行
protected-mode no
`bind 127.0.0.1`
requirepass password
