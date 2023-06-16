配置下载源,在设置-docker engine里修改json文件
 "registry-mirrors": [
    "https://docker.mirrors.ustc.edu.cn/",
    "https://hub-mirror.c.163.com",
    "https://registry.docker-cn.com"
  ]
端口占用,不懂
Error response from daemon: Ports are not available: exposing port TCP 0.0.0.0:3307 -> 0.0.0.0:0: listen tcp 0.0.0.0:3307: bind: An attempt was made to access a socket in a way forbidden by its access permissions.

使用 netsh interface ipv4 show excludedportrange protocol=tcp 查看哪些端口被管制了

暂时用1488端口
docker run --name mysqlA -p 1488:1488 -e MYSQL_ROOT_PASSWORD=123456 mysql

执行 docker exec -it mysqlA /bin/bash 进入bash

dockerdesktop 里的镜像的配置文件存哪里了,如何修改?
使用docker cp mysqlA:/etc/my.cnf C:/java/docker/mysql/conf 将文件复制到本地,修改,重新发布
   在 [mysqld] 下添加 port=1488 即可

mysql -uroot -p 输入密码登录控制台


服务启动成功但是访问不到,试试换个端口号

为啥好多原始端口号都访问不了


如何设置 映射 (图形化方式)
2023-01-19 00:08:08 /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
2023-01-19 00:08:08 /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
2023-01-19 00:08:08 /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
2023-01-19 00:08:08 10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf is not a file or does not exist
2023-01-19 00:08:08 /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
2023-01-19 00:08:08 /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
2023-01-19 00:08:08 /docker-entrypoint.sh: Configuration complete; ready for start up
2023-01-19 00:08:08 2023/01/18 16:08:08 [emerg] 1#1: open() "/etc/nginx/nginx.conf" failed (2: No such file or directory)
2023-01-19 00:08:08 nginx: [emerg] open() "/etc/nginx/nginx.conf" failed (2: No such file or directory)

### 命令
docker run 
  **-t:** 在新容器内指定一个伪终端或终端。
  **-i:** 允许你对容器内的标准输入 (STDIN) 进行交互。
  **-d:** 后台运行
  
docker stop id/name
docker start id/name
docker ps 
docker logs
docker top 来查看容器内部运行的进程
**docker inspect** 来查看 Docker 的底层信息

docker search httpd 搜索镜像

docker rmi 删除镜像
docker rm -f 删除容器


apt-get update
apt-get install iputils-ping/vim/.......

### Dockerfile 
是一个用来构建镜像的文本文件，文本内容包含了一条条构建镜像所需的指令和说明。

### Compose 
是用于定义和运行多容器 Docker 应用程序的工具。

docker ps -a 显示未启动的容器

docker commit -a -m 现有容器ID 保存的名称    -- 将容器保存成镜像?

docker save -o mysql5.7.tar.gz mysql5.7     打包镜像

docker load -i mysql5.7.tar.gz  加载镜像

docker rmi -f `docker images -q`  删除所有镜像