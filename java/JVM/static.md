静态成员（方法或属性）是类的成员存放在==方法区==中，类可以直接调用（是属于类的静态成员，当然对象也可以调用，只是说你可以使用而已）；实例成员是对象的成员，存放在==堆==中，只能被对象调用。
重写的目的在于根据创造对象的所属类型不同而表现出多态。因为静态方法无需创建对象即可使用。没有对象，重写所需要的“对象所属类型” 这一要素不存在，因此无法被重写。
方法重写时基于运行时动态绑定的,而static方法是编译时静态绑定的.
[重定义而不是重写](https://blog.csdn.net/gao_zhennan/article/details/72892946#:~:text=%E7%AD%94%E6%A1%88%E5%BE%88%E6%98%8E%E7%A1%AE%EF%BC%9Ajava%E7%9A%84,%E8%80%8C%E8%A1%A8%E7%8E%B0%E5%87%BA%E5%A4%9A%E6%80%81%E3%80%82)

静态方法不能访问非静态成员

static 不能修饰局部变量

static代码块  
static代码块在jvm加载类的时候会自动执行，如果static代码块有多个，JVM将按照它们在类中出现的先后顺序依次执行它们，每个代码块只会被执行一次。

### 静态内部类与普通内部类的区别

[[静态内部类]]相对与外部类是独立存在的，在静态内部类中无法直接访问外部类中变量、方法。如果要访问的话，必须要new一个外部类的对象，使用new出来的对象来访问。但是可以直接访问静态的变量、调用静态的方法;
普通内部类作为外部类一个成员而存在，在普通内部类中可以直接访问外部类属性，调用外部类的方法。
如果外部类要访问内部类的属性或者调用内部类的方法，必须要创建一个内部类的对象，使用该对象访问属性或者调用方法。
如果其他的类要访问普通内部类的属性或者调用普通内部类的方法，必须要在外部类中创建一个普通内部类的对象作为一个属性，外部类可以通过该属性调用普通内部类的方法或者访问普通内部类的属性
如果其他的类要访问静态内部类的属性或者调用静态内部类的方法，直接创建一个静态内部类对象即可。

