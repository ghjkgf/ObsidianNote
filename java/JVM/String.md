内部定义了 final char[] value,用于存储字符串数据
不可变性，不会对原有字符串重新赋值

https://blog.csdn.net/HD243608836/article/details/79966025
String s1 = new String("myString");
和 
字面量赋值
String s1 = "myString";     常量池

![](https://gss0.baidu.com/-fo3dSag_xI4khGko9WTAnF6hhy/zhidao/wh%3D600%2C800/sign=3ddbeef3f3dcd100cdc9f02742bb6b28/7aec54e736d12f2ebf24ea9e44c2d5628535682e.jpg)

第一种方式通过关键字new定义过程：在程序编译期，编译程序先去字符串常量池检查，是否存在“myString”,如果不存在，则在[[常量池]]中开辟一个内存空间存放“myString”；如果存在的话，则不用重新开辟空间，保证常量池中只有一个“myString”常量，节省内存空间。然后在[[内存堆]]中开辟一块空间存放new出来的String实例，在栈中开辟一块空间，命名为“s1”，==存放的值为堆中String实例的内存地址==，这个过程就是将引用s1指向new出来的String实例

第二种方式直接定义过程：在程序编译期，编译程序先去字符串常量池检查，是否存在“myString”，如果不存在，则在常量池中开辟一个内存空间存放“myString”；如果存在的话，则不用重新开辟空间。然后在栈中开辟一块空间，命名为“s1”，==存放的值为常量池中“myString”的内存地址==

- **这也就是有道面试题：**

 **String s = new String(“xyz”); 产生几个对象？一个或两个，如果常量池中原来没有 ”xyz”, 就是两个**
 

## equals和==
- ``==比较的是内存地址,引用
- `equals未重写时相当于==,重写后只比较值
- `String,BigSet,Date,File都对equals进行了重写

![[Pasted image 20221107210905.png]]
