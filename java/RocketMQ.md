### windows 安装
https://dlcdn.apache.org/rocketmq/5.0.0/rocketmq-all-5.0.0-bin-release.zip
配置系统环境变量
    变量名：ROCKETMQ_HOME
    变量值：MQ解压路径\MQ文件夹名
进入bin,启动cmd,执行 
    start mqnamesrv.cmd
    start mqbroker.cmd -n 127.0.0.1:9876 autoCreateTopicEnable=true
下载rocketmq插件
    git clone https://github.com/apache/rocketmq-externals.git
    dashboard在新版独立了 https://github.com/apache/rocketmq-dashboard
编辑src\main\resources下的yml或者properties文件
![[Pasted image 20230127233822.png]]
进入rocketmq-dashboard或者\rocketmq-externals\rocketmq-console,执行
    mvn clean package -Dmaven.test.skip=true
进入 target 文件夹,执行 java -jar X.jar
浏览器输入 127.0.0.1:port

### docker desktop 安装
使用docker-compose
