CREATE OR REPLACE FORCE 函数/过程/游标 cursor/触发器/视图 view
extract 提取year/month/...
using(x) 替换 on a.x= b.x

PL/SQL 

v_posting_id         number := 0 ;
v_rate               number(5, 4) ;				五位数,小数点前1位,后4位

定义变量的位置 :过程/游标

游标作用:	
		遍历结果集,不会随数据库而改变
					
   变量名      游标名%rowtype;			 ==表示该类型为行数据类型==
   
![[Pasted image 20210726105015.png]]

1、%NOTFOUND。表示游标获取数据的时候是否有数据提取出来，没有数据返回TRUE，有数据返回false。经常用来判断游标是否全部循环完毕，如案例1%NOTFOUND为true的时候，说明循环完毕，跳出LOOP循环。

2、%FOUND。正好和%NOTFOUND相反，当游标提取数据值时有值，返回TRUE，否则返回FALSE。

3、%ISOPEN。用来判断游标是否打开。

4、%ROWCOUNT。表示当前游标FETCH INTO获取了多少行的记录值，用来做计数用的。

substring("string",start,length);						截取,从1开始
charindex('char',"string");									定位

select * from LDMENU start with NODECODE in('9546','9547') connect by prior NODECODE=PARENTNODECODE;		==查询自己及其所有后代==

select * from table for update;				立即开启事务
select a.*,rowid from table;					只有更改数据后,才开启事务

(+)  表示外连接，并且总是放在非主表的一方

inner join  (     ,    为隐式内连接)

left join 
right join 

on 和 where 的区别

join on 后面不能直接使用 or语句,可以用in

<font color="#483D8B">cmd登录</font>
	sqlplus /nolog
	conn bonus/bonus@10.100.252.111:1521/bonus

execute immediate                                    --DDL（数据定义语言）在存储过程里需要的语句

#### char 和 varchar 的区别
 定长       不定长 variety
 
#### 创建索引注意点

#### TRUNCATE 和 DELETE 的区别

从逻辑上说，TRUNCATE 语句与 DELETE 语句作用相同，但是在某些情况下，两者在使用上有所区别。  

-   DELETE 是 DML 类型的语句；TRUNCATE 是 DDL 类型的语句。它们都用来清空表中的数据。
-   DELETE 是逐行一条一条删除记录的；TRUNCATE 则是直接删除原来的表，再重新创建一个一模一样的新表，而不是逐行删除表中的数据，执行数据比 DELETE 快。因此需要删除表中全部的数据行时，尽量使用 TRUNCATE 语句， 可以缩短执行时间。
-   DELETE 删除数据后，配合事件回滚可以找回数据；TRUNCATE 不支持事务的回滚，数据删除后无法找回。
-   DELETE 删除数据后，系统不会重新设置自增字段的计数器；TRUNCATE 清空表记录后，系统会重新设置自增字段的计数器。
-   DELETE 的使用范围更广，因为它可以通过 WHERE 子句指定条件来删除部分数据；而 TRUNCATE 不支持 WHERE 子句，只能删除整体。
-   DELETE 会返回删除数据的行数，但是 TRUNCATE 只会返回 0，没有任何意义。

