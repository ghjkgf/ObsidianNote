各类型长度未明确定义

signed 和 unsigned 进行运算，自动转为 unsigned

### 分离式编译
extern   声明不定义
extern 语句若包含初始值，则变成定义,在函数内部这样操作将引发错误.

变量只能被定义一次,可多次声明.

.h 和 .cpp 文件有啥关系(clion里)

:: 作用域符左侧为空时,则值为全局变量.

引用 &      (就是别名)
    引用不是对象,因此不能定义指向引用的指针
```cpp
int val = 10;
int &val1 = val;
```

指针 *
    指针本身就是一个对象;
    定义时无须赋初值
```cpp
int *ip1,*ip2;

int val = 42;
int *p = &val;   取址运算符 &
cout << *p;      取值操作符 *

int *p1 = nullstr;   空指针的三种写法
int *p2 = 0;        
int *p3 = NULL;

void*可以存放任意类型对象的地址

指针的指针
int ival =10;
int *pi = &ival;
int **ppi = &pi;

指向指针的引用
int i = 42;
int *p;
int *&r = p;   // 为啥不是&*r
                // 从右往左读
r = &i;
*r = 0;


```

```
