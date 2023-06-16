https://python.iitter.com/other/59215.html

传参      rest client组件里传参;

收参      表输入 收参;

不传的话如何设置默认值

使用http方式 url里携带参数可以正常使用,
使用pan.bat /param  ,必须设置 ctrl+T: 命名参数

一个参数都不需要,只要建个etl表,
kettle_task
一行代表一个表的执行,存表名,limit 值,最后执行时间,

pan.bat /file:C:\Users\hougu\Desktop\kettleResources\转换2.ktr "/param:size=100"
自定义参数必须在双引号里

命名参数和变量的区别

carte ip port

中文乱码: 需要修改Kettle的全局配置文件/.kettle/kettle.properties中Servlet字符集编码参数。  
KETTLE_DEFAULT_SERVLET_ENCODING = UTF-8;并重启carte
KETTLE_EMPTY_STRING_DIFFERS_FROM_NULL=Y  使空字符串不为null

/opt/pentaho/data-integration/.kettle    docker路径
/root/.kettle     linux root用户路径
/home/spd/.kettle      普通用户路径     
使用 ls -al 才显示      ls -l 等价于 ll
http组件不能作为输入

sql脚本不受连接顺序影响,会在任务启动时执行
当选中该步骤中的 "单独执行每一行" 选项时,则不会提前执行

当前任务未执行完毕时,事务即未结束

![[kettle多作业可以共享变量.png]]

[kettle自定义输出json_kettle json输出_紫蝶郎的博客-CSDN博客](https://blog.csdn.net/zidielang/article/details/118867911)
在kettle里使用了java

[马进举的个人空间 - OSCHINA - 中文开源技术交流社区](https://my.oschina.net/majj)
看一些kettle 的博客


传参      rest client组件里传参;

收参      表输入 收参;

不传的话如何设置默认值

使用http方式 url里携带参数可以正常使用,
使用pan.bat /param  ,必须设置 ctrl+T: 命名参数

一个参数都不需要,只要建个etl表,
kettle_task
一行代表一个表的执行,存表名,limit 值,最后执行时间,
'
spd@dbhs@ysg

过滤记录

数据库连接

获得变量

增加常量  add constants

字段选择

更改数据发送方文件后,需重启carte

https://blog.csdn.net/xiaosemei/article/details/78563146  日志存库

D:\kettle-pdi\data-integration\logs  spoon.log 和 pdi.log 区别?

docker run -it -v /home/spd/kettleFile:/opt/pentaho/data-integration/kettleFile -p 8787:8787 c54fe2665161 /bin/bash
docker run -it -v C:\Users\hougu\Desktop\kettleResources:/opt/pentaho/data-integration/kettleFile -p 8787:8787 c54fe2665161 /bin/bash

COPY Carte.sh /opt/pentaho/data-integration/
RUN chmod +x /opt/pentaho/data-integration/Carte.sh
curl ifconfig.me            113.128.203.190

http://127.0.0.1:8098/kettle/executeTrans/?trans=/opt/pentaho/data-integration/kettelFile/purchase_order.ktr&size=20&starttime=2023-06-10 10:37:29

http://127.0.0.1:8098/kettle/executeTrans/?trans=C:/Users/hougu/Desktop/kettleResources/purchase_order.ktr

http://test.etl.dbhs.com.cn/kettle/executeTrans/?trans=/opt/pentaho/data-integration/kettelFile/purchase_order.ktr

#!/bin/bash

nohup ./carte.sh 192.168.1.31 8787 > carte.log 2>&1 &


#!/bin/bash

# 获取正在运行的 Carte 进程的 PID
PID=$(pgrep -f "carte.sh")

# 如果 PID 存在，则停止 Carte 进程
if [[ -n $PID ]]; then
    echo "Stopping Carte..."
    kill $PID
    echo "Carte stopped."
else
    echo "Carte is not running."
fi

carte 调java,杀死 carte 后,java不停,仍占端口

netstat -anop|grep 8787  -p 显示进程id;
top 命令列出所有进程 command

http://test.etl.dbhs.com.cn/kettle/executeTrans/?trans=/home/spd/kettleFile/purchase_order.ktr&size=20&starttime=2023-06-10

更改位置
源   表输入;json 输出
目的地   表输入;rest client; json input;插入/更新; add constants;更新		


工作流串联是 按医院还是按表名
在 kettleFile文件夹里放这个文件,存放医院名
ktrConfig.properties 