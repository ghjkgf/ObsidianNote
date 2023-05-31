也是[[容器]],管理着bean的生命周期

实现了简单工厂的设计模式,通过调用getBean传入标识生产一个Bean

有非常多的实现类,最强大的是DefaultListableBeanFactory,Spring底层使用的就是它