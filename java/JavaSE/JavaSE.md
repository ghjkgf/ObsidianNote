break语句出现在多层嵌套的语句块中时，可以通过标签指明要终止的是
哪一层语句块
```java
label1: { ……
label2:     { ……
label3:          {……
                            break label2;
                     }
                }
            }
```
continue类似;

return： 它的功能是结束一个方法。 当一个方法执行到一个return语句时，这个方法将被结束。
 与break和continue不同的是，return直接结束整个方法，不管
这个return处于多少层循环之内.


注意特殊写法情况：int[] x,y[]; x是一维数组，y是二维数组。

Java中多维数组不必都是规则矩阵形式,比如二维数组里的每一个一维数组长度不一定相等

排序算法的选择:  [[十大排序]]
- 若n较小(如n≤50)，可采用直接插入或直接选择排序。
当记录规模较小时，直接插入排序较好；否则因为直接选择移动的记录数少于直接插入，应选直接选择排序为宜。
- 若文件初始状态基本有序(指正序)，则应选用直接插入、冒泡或随机的快速排序为宜；
- 若n较大，则应采用时间复杂度为O(nlgn)的排序方法：快速排序、堆排序或
归并排序


我们也可以不定义对象的[[句柄]]，而直接调用这个对象的方法。这样的对象叫做==匿名对象==。
 如：new Person().shout();
 
![[Pasted image 20220518001927.png]]

### 重载 :只和参数列表有关,与返回类型无关
     Java的重载是可以包括父类和子类的，即子类可以重载父类的同名不同参数的方法
     即子类从父类继承的方法和子类独有的方法构成重载

Varargs(variable number of arguments)机制
 
//JDK5.0开始：采用可变个数形参来定义方法，传入[0,n]个同一类型变量
```java
    public static void test(int a ,String...books);
```

Java里方法的参数传递方式只有一种：值传递。即将实际参数值的副本
（复制品）传入方法内，而参数本身不受影响。

关于变量的赋值:
- 变量为基本数据类型,赋值的是变量所保存的数据值;
- 变量为引用类型,赋值的是变量所保存的数据的地址值.

```java
public void println(char[] x) {  
    if (getClass() == PrintStream.class) {  
        writeln(x);  
    } else {  
        synchronized (this) {  
            print(x);  
            newLine();  
        }  
    }}
```
println 当参数为char数组时,情况特殊,会直接将其输出为字符串,而不是地址值;

![[Pasted image 20220518111434.png]]

根据参数不同，构造器可以分为如下两类：
- 隐式无参构造器（系统默认提供）
- 显式定义一个或多个构造器（无参、有参）
注意：
- Java语言中，每个类都至少有一个构造器
- 默认构造器的修饰符与所属类的修饰符一致
- 一旦显式定义了构造器，则系统不再提供默认构造器
- 一个类可以创建多个重载的构造器
- 父类的构造器不可被子类继承

==JavaBean==是一种Java语言写成的可重用组件。
所谓javaBean，是指符合如下标准的Java类：
- 类是公共的
- 有一个无参的公共的构造器
- 有属性，且有对应的get、set方法
  用户可以使用JavaBean将功能、处理、值、数据库访问和其他任何可以
用Java代码创造的对象进行打包，并且其他的开发者可以通过内部的JSP
页面、Servlet、其他JavaBean、applet程序或者应用来使用这些对象。用
户可以认为JavaBean提供了一种随时随地的复制和粘贴的功能，而不用关
心任何改变。

UML 类图
![[Pasted image 20220518112331.png]]

![[Pasted image 20220518113322.png]]

### this
使用this访问属性和方法时，如果在本类中未找到，会从父类中查找

![[Pasted image 20220518113605.png]]
super类似,同样也只能放首行,因此this/super只能二选一
默认调了super(无参);
在类的多个构造器中,至少有一个类的构造器中使用了super

### 包装类
- Integer 里的 [-128,127]问题,当使用的数据在这个范围内,是直接取的缓存,而不是通过new 得到的.

```java
boolean flag = true;  
Object o1 = flag ? new Integer(1) : new Double(2.0);        // 三目运算会在编译时调整双方类型  
System.out.println(o1);  
System.out.println(o1.getClass());   //Double
```

作用:将字符串变为基本数据类型
父类是Number

#### 继承
子类不能直接访问父类中私有的(private)的成员变量和方法。

_优先级：父类静态代码块 > 子类静态代码块 > 父类构造代码块 > 父类构造器 > 子类构造代码块 > 子类构造器_

#### 重写
子类重写的方法必须和父类被重写的方法具有相同的方法名称、参数列表
子类重写的方法使用的访问权限不能小于父类被重写的方法的==访问权限==
子类重写的方法的返回值类型不能大于父类被重写的方法的==返回值类型==
子类不能重写父类中声明为private权限的方法
子类方法抛出的异常不能大于父类被重写方法的异常
- 子类与父类中同名同参数的方法必须
  同时声明为非static的(即为重写)，
  或者同时声明为static的（不是重写）。
  因为static方法是属于类的，子类无法覆盖父类的方法

#### super
当子父类出现同名成员时，可以用super表明调用的是父类中的成员
==super的追溯不仅限于直接父类==
- 子类中所有的构造器默认都会访问父类中空参数的构造器
- 当父类中没有空参数的构造器时，子类的构造器必须通过this(参
数列表)或者super(参数列表)语句指定调用本类或者父类中相应的
构造器。同时，只能”二选一”，且必须放在构造器的首行

创建子类时,调用了父类的构造器,但只new了(创建了)一个对象.


#### 多态(父类的引用指向子类的对象)
Java引用变量有两个类型：编译时类型和运行时类型
编译时类型由声明该变量时使用的类型决定，
运行时类型由实际赋给该变量的对象决定。
简称：编译时，看左边；运行时，看右边。
- 若编译时类型和运行时类型不一致，就出现了对象的多态性(Polymorphism)
- 多态情况下，
        “看左边”：看的是父类的引用（父类中不具备子类特有的方法）
        “看右边”：看的是子类的对象（实际运行的是子类重写父类的方法）
   
![[Pasted image 20221104092210.png]]

子类可以彻底覆盖父类的方法;
但是不能覆盖父类中定义的实例变量,编译运行时看左边.


### 接口与抽象类
1. 接口定义的属性自带 public static final
2. 当父类和接口的属性冲突时,super.a 和 A(接口名).a 可以区分
3. jdk8以后,接口里可以定义static方法和default方法
4. 当父类和接口的方法冲突时,且子类未重写,类优先原则
5. 要想调用接口的方法,则使用
A(接口名).super.method
6. 同时实现的多个接口方法冲突时,报错



#### 虚拟方法调用(Virtual Method Invocation)

子类中定义了与父类同名同参数的方法，在多态情况下，将此时父类的方法称为虚拟方法，父
类根据赋给它的不同子类对象，动态调用属于子类的该方法。这样的方法调用在编译期是无法
确定的。

x instanceof A：检验x是否为类A的对象，返回值为boolean型。
 要求x所属的类与类A必须是子类和父类的关系，否则编译错误
用于能否向下转型的判断

== | equals
---|---
可以比较基本类型和引用类型 | 只能比较引用类型
默认语法| 继承自Object 类的方法

equals如果没有重写,和 == 作用一样,都是比较内存地址

在进行String与其它类型数据的连接操作时，自动调用==toString()==方法
```java
Date now=new Date();
System.out.println(“now=”+now); //相当于
System.out.println(“now=”+now.toString());
```



#### 异常
重写方法不能抛出比被重写方法范围更大的异常类型。
在多态的情况下， 对方法的调用-异常的捕获按父类声明的异常处理。


### 比较器

自然排序 ：实现 comparable 接口
定制排序 ：实现 comparator 接口
       jdk中未实现 comparable接口的
       不想用之前的排序规则
       临时使用

### 迭代器

Iterator 接口
    Next() ; HasNext();
    Remove()
集合对象每次调用iterator()方法都得到一个全新的迭代器对象,默认游标都在集合的第一个元素之前.
使用remove之前必须用过next;
不能连续使用remove

### foreach
```java
String[] arr = new String[] {"aaa","bbb","ccc"};  
for (String s : arr) {  
    s = "fasfd";    // 不会改变string数组里的内容  
}  
for (String s : arr) {  
    System.out.println(s);  
}
```

Properties 是 Hashtable的子类,用于处理属性文件
