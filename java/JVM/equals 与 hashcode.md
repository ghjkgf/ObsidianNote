只要重写equals,就应该重写hashcode

set存储的对象必须重写二者

当对象作为map的键时,需要重写

## 为什么需要hashcode?
hashcode方法比equals快;
hashCode()返回一个int类型，两个int类型比较起来要快很多。
哈希容器使用get方法时,先通过hashcode判断有无,再通过equals判断