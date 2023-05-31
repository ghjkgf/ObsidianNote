Unified modeling language
统一建模语言
![[Pasted image 20210121115118.png]]
Dependency 依赖	箭头实线
Association 关联		单实线
Generalization 泛化(继承)  (父:非抽象)  三角形实线
Realization 实现		(父:抽象)	三角形虚线
Aggregation 聚合
Composite 组合

简单来讲，组合是一种较为紧密的关系，从生命周期上看，部分和整体是共存亡的关系。 实心菱形
聚合则是一种较为松散的关系，部分和整体的生命周期未必一致。 	空心菱形

在实际代码中，<span style="color:red;">组合关系中，部分的实例化在整体中进行。</span>聚合关系中，部分的实例化过程在整体外进行，然后通过某种方式注入给整体。
另一种表现可能是，组合是静态聚集，聚合是动态聚集。

级联删除,就是组合