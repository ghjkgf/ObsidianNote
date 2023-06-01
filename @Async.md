真难......

@Async 在方法上
@EnableAsync()
	1. 被代理的类被注入时,需要使用 接口类型
	2. 设置@EnableAsync(proxyTargetClass = true)
	ps. 当设置某一注解属性后仍不生效,先看看项目里有没有其他地方相同注解优先作用

同类方法调用,代理不生效
需要设置
@EnableAspectJAutoProxy(proxyTargetClass = true, exposeProxy = true)  // 在类上
((MyInterceptor) AopContext.currentProxy()).method()

@Async还需要多加一步 @transactional
[@Async分析exposeProxy=true不生效原因_async expose_lw_yang的博客-CSDN博客](https://blog.csdn.net/Sophisticated_/article/details/102793703)

```java
@Transactional  必须
@Override  
public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {  
    String[] needTransfers = {"/heartbeat"}; // todo  
    String url = request.getRequestURL().toString();  
    for (String needTransfer: needTransfers) {  
        if(url.contains(needTransfer)){  
            try {  
                // processUseRestTemplate(request,url);  
                ((MyInterceptor) AopContext.currentProxy()).processUseRestTemplate(request,url);  
            } catch (Exception e) {  
                System.out.println(e);  
            }  
            break;  
        }  
    }   
}

@Async 
public void processUseRestTemplate(HttpServletRequest request, String url){  
    ...... 
}
```
所有,直接在最外层加@Async....