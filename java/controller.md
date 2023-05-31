实现此接口的类获得控制器的功能(返回一个modelAndView)
- 1.添加数据	addObject
- 2.设置路径   setViewName

@Controller

如果返回值是String,并且有对应页面可以跳转,就会被解析器解析

多个方法可以复用同一个页面,但是页面内容可以不一样:	
	控制器与视图之间是弱耦合关系

重定向
	return "redirect:/X.jsp";

设置前端对应参数
	@RequestParam("")
	
ModelMap 实现了linkedHashMap
Model精简了ModelMap

乱码问题
配置过滤器	/* 才能作用到jsp页面