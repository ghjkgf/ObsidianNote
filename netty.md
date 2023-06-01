异步,基于事件驱动的网络应用框架,基于NIO

## I/O模型
采用什么通道处理连接请求
### BIO
同步阻塞,一个连接一个线程,服务器炸了,线程占用资源

### NIO
同步非阻塞,多路复用器 Selector,一个线程处理多个请求
面向缓冲区,面向块
### AIO
异步非阻塞,异步通道,Proactor模式,有效的请求才启动线程,

### 缓冲区Buffer
本质上是一个可以读写数据的内存块,可以理解成一个容器对象(含数组)
Channel提供从文件/网络读取数据的渠道,但是必须经过Buffer

| 属性名   | 含义                                             |
| -------- | ------------------------------------------------ |
| capacity | 容量,不可变                                      |
| limit    | 缓冲区的当前终点,不可对超过极限的位置读写,可修改 |
| position | 下一个读写的位置                                 |
| mark     | 标记                                             |
| hb       | heap buffer                                      |
|          |                                                  |
 ```java 
 //翻转操作
 public Buffer flip() {  
    limit = position;  // limit从capacity变成了实际写入的量
    position = 0;  // 从头开始读
    mark = -1;  
    return this;
}
```

### 通道 Channel
同时读写,异步
 