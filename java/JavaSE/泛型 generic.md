![[Pasted image 20221108085709.png]]

![[Pasted image 20221108090430.png]]
![[Pasted image 20221108090721.png]]

```java
public class Order<T> {  
    String orderName;  
    int orderId;  
    T sth;      // 要想使用自定义泛型,需要在类明处标记  
}
```

![[Pasted image 20221108095607.png]]

![[Pasted image 20221108095658.png]]

泛型方法
和所属类或者接口是否为泛型 无关
在方法中出现了泛型的结构,泛型参数与类的泛型参数没有任何关系

![[Pasted image 20221108132300.png]]
public 后面紧跟着的 `<E>` 是告诉编译器使用了泛型,而非某个具体的类是E

```java
public static <E> List<E> copyFrom(E[] arr){  
    // 泛型参数可以声明为静态的; 因为泛型参数是在调用方法时确定的,而非实例化类时确定  
    return new ArrayList<E>();  
}
```

`<?> 通配符`
由于`List<Child>`不是`List<Parent`的子类,因此需要将`<?> `设置为共同父类;
可以将其放在方法的参数位置,就可以复用了
其只能添加null元素;

`<? super A>` 表示 A类及上面的父类;
插入A-child不受限

`<? extends A>` 表示 A类及下面的子类;
插入受限