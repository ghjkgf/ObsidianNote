	执行流程
 
 model view [[controller]] [[restful风格]]
 ![[Pasted image 20210203215750.png]]
 ![[Pasted image 20210203215811.png]]
 
 确保artifact包含有依赖,否则报404
 - 1.引入依赖
 - 2.配置dispatcherServlet
 	- servlet
		- servlet-name
		- servlet-class
		- init-param		绑定springmvc的配置文件
			- param-name
			- param-value
		- load-on-start 	设置启动级别
 	- servlet-mapping
 - 3.xml文件配置
 	- 处理器映射器
 	- 处理器适配器
 	- 视图解析器
		- class:InternalResourceViewResolver
			- property 	 prefix
								suffix
- 4.编写controller
	重写方法;返回一个modelAndView
		- 业务代码
		- 视图跳转


##完全注解开发
- 开启包扫描 :<context:component-scan base-package="com.kuang.controller"/>
- 过滤静态资源:<mvc:default-servlet-handler/>
- 配置handlerMapping & handlerAdapter:<mvc:annotation-driven/>
- 视图解析器不变
```xml
<bean class\="org.springframework.web.servlet.view.InternalResourceViewResolver" id\="InternalResourceViewResolver"\>  
 <property name\="prefix" value\="/WEB-INF/jsp/"/>  
 <property name\="suffix" value\=".jsp"/>  
</bean>
```

![[Pasted image 20210204204728.png]]
![[Pasted image 20210204205216.png]]

MVC与MVVM
                    viewModel  双向绑定

![[Pasted image 20221110081844.png]]

出现404:
    Project Structures->Artifacts->在WEB-INF下创建lib目录,将jar包复制过来.

- 使用配置文件 
    实现mvc的Controller接口的类获得控制器功能
    处理请求并且返回一个模型与视图对象
- 使用注解
    - 可以在一个文件中创建多个controller
    - @Controller 标记类中的方法返回值为string时,默认视图解析器解析(拼接url)

post get 

重定向|转发(默认)
---|---
url变|不变
return "text"; | return "redirect:/index.jsp";

