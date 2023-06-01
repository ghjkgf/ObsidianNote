### 注解和切面

src/main/java/com/dbhs/cloud/common/annotation/DataAuth.java
src/main/java/com/dbhs/cloud/common/security/annotation/InnerAuth.java

@Test
不需要测试的方法注释掉,避免报错  Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException
默认不会更改数据库数据,可以加上 @Rollback(false) 更改,改完后出错也不会回滚了....
Gyro debug 仍然不会更改数据库....

[java为什么不允许父类强转子类？](https://www.zhihu.com/question/471226793)

注解@Order或者接口Ordered的作用是定义Spring IOC容器中Bean的执行顺序的优先级，而不是定义Bean的加载顺序，Bean的加载顺序不受@Order或Ordered接口的影响；