
## 什么是Carte

​	Carte是一个轻量级的web服务，允许远程请求HTTP进行监控、启动、停止在Carte服务上运行的任务（作业或转换）。运行Carte的服务器在kettle术语里称为slave server。

​	KettlePack从0.5.0开始支持Carte执行任务。



### 优点

- 分担KettlePack执行的任务，KettlePack负责调度，任务执行交由Carte完成

- 可以跨Kettle版本执行任务，Carte集成在data-integration中，是由原生的kettle来执行

  如：执行Kettle9或更新版本所创建的任务

- 可解决个别插件在Spoon中可执行，但在KettlePack中不能执行的问题

- 网络隔离问题

  例：有三台服务器，①KettlePack服务器、②中间服务器、③数据库服务器

  如果①和③有网络隔离，②和③的网络相通，

  而任务需要访问③，那么可以在②上启动一个Carte服务，将任务交由②来执行

  

### 缺点

- 需要另外配置、启动Carte服务
- 对于Carte主服务交给子服务执行任务的情况 ，无法获取子服务中执行的日志
- 对【文件管理】、【文件资源库】方式有不支持的情况，详见【Carte执行的局限性】





## 启动Carte服务



### 方式一

```shell
#进入kettle目录
cd data-integration

#windows
Carte.bat ip port
#例：
Carte.bat 192.168.x.x 8080

#linux
./carte.sh ip port
#例：
./carte.sh 192.168.x.x 8080
```

### 方式二

编辑data-integration/pwd/carte-config-xxxx.xml

```shell
  #进入kettle目录
  cd data-integration
  
  #windows
  Carte.bat pwd\carte-config-xxxx.xml
  
  #linux
  ./carte.sh pwd/carte-config-xxxx.xml
```

###   注意

- Carte默认用户名、密码为cluster
- 启动Carte服务时请使用IP不要使用localhost，否则只能本机访问
- Carte服务端需要相同的插件库（plugins）
- 如果Carte服务器开启了防火墙，请开放Carte所使用的端口



## 资源库配置

Carte服务器需要配置资源库配置文件：repositories.xml，

因为Carte执行的作业中如果包含了转换，Carte需要从资源库中获取对应转换的内容。



### 文件位置 

USER_HOME/.kettle/repositories.xml

- windows位置： 
  C:\Users\用户名\.kettle\repositories.xml

- linux位置：
  普通用户为：  /home/用户名/.kettle/repositories.xml 
  root用户为： /root/.kettle/repositories.xml

  

### 本地Carte服务配置

KettlePack支持写入到本地资源库配置

可从菜单【资源管理 - 资源库管理 - 生成本地配置】写入本地



### 远程Carte服务配置

需要相同配置的<repository>和<connection>节点

可从菜单【资源管理 - 资源库管理 - 下载配置】，将下载的配置文件放入远程Carte服务器中对应位置 （也可修改）





## Carte执行的局限性



### KettlePack执行Carte任务

| 任务                   |   文件    |   文件    | 文件资源库 | 文件资源库 | 数据库资源库 | 数据库资源库 |
| :--------------------- | :-------: | :-------: | :--------: | :--------: | :----------: | :----------: |
|                        | 本地Carte | 远程Carte | 本地Carte  | 远程Carte  |  本地Carte   |  远程Carte   |
| 转换                   |     √     |     √     |     √      |     √      |      √       |      √       |
| 简单作业（不包含转换） |     √     |     √     |     √      |     √      |      √       |      √       |
| 复杂作业（包含转换）   |     √     |     ×     |     √      |     ×      |      √       |      √       |

  

### Spoon执行Carte任务

| 任务                   |   文件    |   文件    | 文件资源库 | 文件资源库 | 数据库资源库 | 数据库资源库 |
| :--------------------- | :-------: | :-------: | :--------: | :--------: | :----------: | :----------: |
|                        | 本地Carte | 远程Carte | 本地Carte  | 远程Carte  |  本地Carte   |  远程Carte   |
| 转换                   |     √     |     √     |     √      |     ×      |      √       |      √       |
| 简单作业（不包含转换） |     √     |     √     |     √      |     ×      |      √       |      √       |
| 复杂作业（包含转换）   |     √     |     ×     |     √      |     ×      |      √       |      √       |



### 注

- 以上为个人测试结果，测试使用的Spoon版本为8.3.0.0-371，KP版本为0.5.0
- 【本地Carte】：与KettlePack同在一台机器运行的Carte服务
- 【远程Carte】：除【本地Carte】以外的Carte服务
- 从以上两表可看出，<u>数据库资源库</u>为Carte执行任务的最佳选择



## 常见问题



### Carte服务启动后，KP测试连接不成功 

- 检查Carte服务器是否开放对应端口

- 启动Carte服务时请使用IP不要使用localhost，否则只能本机访问

  例本机IP为 192.168.1.100

  请使用<u>Carte.bat 192.168.1.100 8080</u> 启动

  如果使用<u>Carte.bat localhost 8080</u>启动，则只能从本机使用localhost:8080访问

- Carte服务器启动后，可以使用浏览器访问：http://ip:port

  



### Carte执行任务时中文乱码（日志或任务路径）

修改Carte.bat文件，在【pushd %~dp0】下（换行）添加以下代码

```
set OPT= -Dfile.encoding=utf-8
```

Carte.bat完整示例(不含注释部分)：

```shell

setlocal
pushd %~dp0

set OPT= -Dfile.encoding=utf-8
SET OPT=%OPT% "-Dorg.mortbay.util.URI.charset=UTF-8"
SET STARTTITLE="Carte"
SET SPOON_CONSOLE=1

REM set OPT=%OPT% -Djava.security.auth.login.config=%JAAS_LOGIN_MODULE_CONFIG%
REM set OPT=%OPT% -Dloginmodulename=%JAAS_LOGIN_MODULE_NAME%
call Spoon.bat -main org.pentaho.di.www.Carte %*
popd

```



### 修改Carte内存使用

修改Spoon.bat，添加：

```
set PENTAHO_DI_JAVA_OPTIONS="-Xms2048m" "-Xmx4096m" "-XX:MaxPermSize=256m"
```











*by MJP 20210806*