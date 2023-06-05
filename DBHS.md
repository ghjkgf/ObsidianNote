### 禅道
1、禅道访问地址：[http://zentao.gate.bjknrt.com/](http://zentao.gate.bjknrt.com/) 
2、用户名和密码：zhaosenlin/111111

### gitlab 
zhaosenlin@dbhs.com.cn
P@ssw0rd

nacos / nacos

### 云平台
60.205.186.245:10241

后端执行 maven install,生成jar包,
(第一次需要先打包 猴子和老鼠,后续不用)
放在 /home/spd/deploy_dir ,执行 .sh脚本
前端先执行 npm run build:prod,生成dist文件夹
传到/home/spd下,切root用户,挪到/home/spd/cloud-platform-proxy 
文件夹重命名为public ,执行 npm run start

测试地址
https://dbhs-cloud-241.gate.bjknrt.com/

跳转
ssh -p 10240 spd@192.168.1.240
scp -P 10240 /home/spd/cloud-platform.zip spd@192.168.1.240:/home/spd/cloud-platform.zip

### ETL

更改 etl-0.0.2-SNAPSHOT.jar\BOOT-INF\classes\config\ 下的 client.properties文件
pushchargetohis

老版ftp    /产品发布/spd/程序发布/程序发布
压缩包里放jar包和操作指南
老版本etl程序压缩包命名规则： etl-server-20230302.zip etl-server是固定的，后面是打包日期
ftp
101.201.142.93              端口不填
/产品发布/新版spd/程序发布/etl程序/通用   备份路径

/产品发布/新版spd/程序发布/程序发布    发布路径
用户名：zhaosenlin 密码：7Z4Y903d

更改 build.sh里的版本号

mlx  111111 监控 定时任务 新增

etl服务端操作指南
部署方式：
1.如果是首次部署先修改application.properties文件里面的数据库相关配置和spd地址
2.首次部署将application.properties，etl-0.0.2-SNAPSHOT.jar，startup.sh，stop.sh四个文件拷贝到linux服务器上面，二次部署只需要更新etl-0.0.2-SNAPSHOT.jar
3.切换root用户，并进入etl部署文件夹。命令： cd /opt/service/java/etl ，如果首次部署需要创建文件夹 cd  /opt/service,mkdir java,cd  java,mkdir etl。
4.执行命令：source /etc/profile
4.非首次部署需要停止etl服务 ./stop.sh
5.将文件移动到部署文件夹中 mv /home/spd/etl-0.0.2-SNAPSHOT.jar . 如果首次部署需要将其余三个文件也移动过来mv /home/spd/application.properties .，mv /home/spd/startup.sh .，mv /home/spd/stop.sh .
6.修改所有文件权限为777。命令： chmod 777 etl-0.0.2-SNAPSHOT.jar 
7.启动服务 ./startup.sh
8.首次部署可能需要开放端口，参考下面命令:查看开放端口和允许端口开放。
9.部署成功后可以通过客户端连接一下看看客户端显示etl版本号证明部署成功

常用命令：
查看etl线程：
 ps -ef|grep etl

杀进程：
kill -9 3557 (3557为线程号)

启动脚本：
 ./startup.sh

停止脚本：
./stop.sh

查看开放端口：
sudo ufw status

允许8088端口开放：
sudo ufw allow 8088


手动启动命令参考（不使用脚本启动，指定时区的参考命令）：
java -Xms4g -Xmx4g -Duser.timezone=Japan -jar etl-0.0.2SNAPSHOT.jar


切换超级管理员
sudo -s

切换普通用户
su 用户名

查看docker 容器
docker ps
docker cp etl-0.0.2-SNAPSHOT.jar spd-etl:/home/spd/etl-0.0.2-SNAPSHOT.jar   // 上传jar包
docker cp spd-etl:/home/spd/etl-0.0.2-SNAPSHOT.jar bak.jar  // 备份
docker restart spd-etl 
docker logs --tail 100 spd-etl    -f 实时日志
docker exec -it spd-etl /bin/bash
![[Pasted image 20230522181531.png]]
使用docker cp 命令将日志拷贝出来
映射的日志 data/spd/logs/spd-etl/

