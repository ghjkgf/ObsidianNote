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