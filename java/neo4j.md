节点     ()
关系     []
属性     {}

"ALTER"
  "CALL"
  "CREATE"
  "DEALLOCATE"
  "DELETE"
  "DENY"
  "DETACH"
  "DROP"
  "DRYRUN"
  "ENABLE"
  "FOREACH"
  "GRANT"
  "LOAD"
  "MATCH"
  "MERGE"
  "OPTIONAL"
  "REALLOCATE"
  "REMOVE"
  "RENAME"
  "RETURN"
  "REVOKE"
  "SET"
  "SHOW"
  "START"
  "STOP"
  "TERMINATE"
  "UNWIND"
  "USE"
  "USING"
  "WITH"
```sql
查询 id = 1 的节点n
match (n) where id(n)=1 return n



创建节点
create (user:User {name:"ghjkgf",age:24})

创建节点列表
unwind [{name:"dog"},{name:"cat"}] AS animal create (n:Animal) set n = animal

创建关系
match (n{name:"a"}),(m{name:"b"})
create (n)-[r:Knows]->(m)

建立关系时设置属性
match (n{name:"a"}),(m{name:"b"})
create (n)-[:朋友{亲密度:3}]->(m)

使用merge,不存在才创建
merge (n:MetroStation {name:"复兴门"}) 
on create set n.lineNo = 1

match (n{name:"a"}),(m{name:"b"})
merge (n)-[:敌人]->(m)

set 更新
merge (n:Person {name:"ghjkgf"})
set n.age = 18

使用预定的参数增加多个属性
unwind[{age:30},{addr:"北京"}] as prop
merge (n:Person {name:"nanke"})
set n+=prop

删除数据
关系解除后才可以delete
match (n) delete n

删掉第二个节点和关系    
match ()-[r:`朋友`]->(m) delete r,m

remove 强制移除
match (n) remove n:Test
match (n{name:"b"}) remove n.age 移除属性

循环语句
with ["a","b","c"] as coll foreach (value in coll | create (:Person{name:value}))

创建索引
create index on :Person(name)

指定使用索引
match (n:Person) 
using index n:Person(name)
where n.name = 'a'
return n as Person

删除索引
drop index on :Person(name)

-- 创建约束
create constraint for (m:MetroStation) 
require m.name is unique

删除约束
drop constraint for (p:Person) 
require p.name is unique

-- with 管道
使用with 可以将上一条查询语句的结果链接起来,用于下一条查询语句中
match (a)-[:Knows]->(b)
with a,count(b) as knows
where knows>0
return a
```

```sql
match p=(n:Person)-[:`同门`]->()
where n.name = "沙悟净"
return p

只读查询结构
```
![[Pasted image 20230107114801.png]]