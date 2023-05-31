repo.spring.io/release/org/springframework/spring/
概念;[[IOC]]容器;[[AOP]];[[JdbcTemplate]];[[事务管理]];5的新特性

IOC:把创建对象交给Spring;
控制反转
==控制==	控制对象的创建的权利,由程序员到IOC容器
==翻转==  由容器帮我们查找及注入依赖对象,对象只是被动的接受依赖对象
DI是实现IOC的一种方式

AOP:不改变源代码,却能增强功能
面向切面
  

方便解耦,简化开发

方便事务操作,封装一些复杂api

源码值得学习

  [[BeanFactory]] 和 [[ApplicationContext]]的关系:
  	后者实现了前者
  	BeanFactory用于生产bean;		--汽车工厂
	applicationcontext不生产bean,而是通知BeanFactory生产bean          --4s店
	后者做的更多:		自动将配置的bean注册;
								加载环境变量
								支持多语言
								实现事件监听
								注册对外扩展点
    前者由于做得少,占用内存小,适用于嵌入式开发
	
	
	
IOC底层原理:xml解析;工厂模式;反射

