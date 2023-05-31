面向切面编程	aspect oriented programming

JDK动态代理
类Proxy
intercept 拦截


连接点:	可以被增强的方法
切入点:	实际被真正增强的方法
通知(增强):		代码部分
	5种类型:	前置,后置,环绕,异常,最终	@Before,@After,@Around,@AfterThrowing,@AfterReturning
切面:		动作,把通知应用到切入点的过程

名称	|备注
---|---
org.springframework.aop.MethodBeforeAdvice(前置通知)	|在方法之前自动执行的通知称为前置通知，可以应用于权限管理等功能
org.springframework.aop.AfterReturningAdvice(后置通知)	|在方法之后自动执行的通知称为后置通知，可以应用于关闭流、上传文件、删除临时文件等功能
org.aopalliance.intercept.MethodInterceptor(环绕通知)	|在方法前后自动执行的通知称为环绕通知，可以应用于日志、事务管理等功能
org.springframework.aop.ThrowsAdvice(异常通知)	|在方法抛出异常时自动执行的通知称为异常通知，可以应用于处理异常记录日志等功能
org.springframework.aop.IntroductionInterceptor(引介通知)	|在目标类中添加一些新的方法和属性，可以应用于修改旧版本程序（增强类）
 

AspectJ:单独框架

切入点表达式:		execution(权限修饰符,返回类型,类全路径,方法名称,参数列表)		``*代表所有
相同切入点提取:在方法上@Point(value= "execution")
多个增强类设置@Order(digit)	digit越小优先级越高
- 注解方式:1.创建被增强类;2.创建增强类;3.配置(context,aop名称空间),开启注解扫描,增强类上@Aspect 4.生成代理对象:<aop:aspectj-autoproxy/>
- xml配置:![[Pasted image 20210131183614.png]]
- 完全注解开发:配置类![[Pasted image 20210131183901.png]]
