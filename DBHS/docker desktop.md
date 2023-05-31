ping host.docker.internal      docker容器内服务使用宿主机服务

docker 会添加内容到hosts文件中
https://www.cnblogs.com/m-finder/p/11592716.html

宿主机 ping docker容器
https://blog.csdn.net/qq_45380083/article/details/124612501

常用操作
https://blog.csdn.net/lit_chicken/article/details/100931717

windows上安装vim    好像安装个gvim就行了....
https://blog.csdn.net/qyhaill/article/details/105425057  配置vim插件等
https://zhuanlan.zhihu.com/p/352566225
 
cli 工具推荐
https://zhuanlan.zhihu.com/p/266032071

### Neo4j
7890,7891

### Nacos
MODE=standalone
8847
docker desktop部署nacos并连接windows宿主机的mysql  https://blog.csdn.net/tyvbpq/article/details/119536749

nacos里可以直接使用vim,靠的啥 


### RocketMQ

#### 通过docker-compose安装RocketMQ
https://blog.csdn.net/sayoko06/article/details/115354427

https://cn.bing.com/search?q=docker-compose&PC=U316&FORM=CHROMN

docker镜像文件的导入导出
https://blog.csdn.net/weixin_42547154/article/details/84107501

### mongo
看docker里的日志,发出请求的ip都是这个172.17.0.1,但是本地ipconfig不是这个
容器的hosts文件只配了 172.17.0.5    dd6212047050(容器id)
本地wsl ifconfig都是 172.23.123.232 