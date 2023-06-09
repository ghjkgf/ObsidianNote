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

http组件不能作为输入