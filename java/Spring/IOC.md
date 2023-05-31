inversion of control
底层原理:	  xml解析
					工厂模式![[Pasted image 20210128093757.png]]
					反射
	![[Pasted image 20210128094654.png]]
	
两个接口
	beanfactory
		![[Pasted image 20210128101834.png]]
		//configurableAppliacationContext用于实现拓展功能
	applicationcontext:一加载配置就创建对象,用
		两个实现类
		![[Pasted image 20210128101341.png]]
	
	name属性过时,等同于id
	默认执行无参构造
DI:dependency inject
<property>注入属性值(set方法)		name:value

<constructor-arg> 设置有参构造	name或者index:value
	
p空间注入(简化set)
	xmlns:p="../beans->p"
	<bean id,class,p:属性a:值1,...p:属性z:值26></bean>
	
字面量:{
	null值:<null/>
	特殊符号:1.转义;2.cdata:	![[Pasted image 20210128113132.png]]
	
- 外部bean
 	ref;
- 内部bean
- 级联赋值{
	1.外部bean形式
	2.运算符. 及getter方法
	
注入数组,list,map
	元素是普通型,对象
	集合作为单元	->util命名空间增加:xmlns与schemaLocation值			[schema:纲要    schedule:时刻表]
	增加<util:list>标签
	
	{普通bean & factoryBean}	配置文件中定义的类型与返回的类型是否必须一致
	步骤:1.创建类,让这个类作为工厂bean,实现接口FactoryBean
			2.实现接口里面的方法,在实现的方法中定义返回的bean类型
作用域:单实例还是多实例
	scope值{singleton,prototype}还有两个,不常用:session,request(web知识)
生命周期:init-method;destroy-method;需要手动销毁:context.close(); 
	后置处理器:
	https://www.jianshu.com/p/f80b77d65d39
	https://juejin.cn/post/6844903969731379208
自动装配(根据属性名称/类型)
	autowire="byName","byTag"
	
	
##注解方式
	位置,类,方法,属性上都可以
	@component
	@service   			service层
	@controller			web层
	@repository			dao层
	引入aop.jar包
	开启组件扫描,指定类	component-scan base-package,多个包用逗号分隔;
	![[Pasted image 20210129194740.png]]
	- 不想扫描整个包中的类:
		1.关掉默认过滤器;
		2.自己设置过滤器
	- 排除扫描某些类
	在类上添加注解,可省略属性值(默认类名首字母小写)
	
注入属性
	@autowired                   根据类型
	@Qualifier								名称			//结合autowired使用
	@Resource							类型||名称
	@Value  注入普通类型属性

	
完全注解开发
	配置类 @configuration	@componentScan(包)
@Configuration  
@ComponentScan(basePackages = {"com.forest.annotationComplete"})  
public class ConfigurationTest {  
  
}
	
ApplicationContext context = new AnnotationConfigApplicationContext(ConfigurationTest.class);  
UserService userService = context.getBean("userService", UserService.class);

	
### 优点
	集中管理对象,对象之间的耦合度降低,方便维护对象
	
	