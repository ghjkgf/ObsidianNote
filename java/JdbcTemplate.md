spring 对jdbc进行封装

- 引入jar包
- 配置数据库连接池

- 创建jdbcTemplate 对象
 id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
 - 注入DataSource
 property name="",ref=""
 - 创建service类,创建dao类,在dao注入jdbcTemplate对象

jdbc:mysql:///company等同于 jdbc:mysql://localhost:3306/company 

Mysql8.0+版本的对应配置：
driverClassName属性对应的值为com.mysql.cj.jdbc.Driver

查询返回对象
	rowMapper接口:根据指定类型,将返回数据进行封装
	使用BeanPropertyRowMapper实现类
	
JdbcTemplate主要提供以下五类方法：  
execute方法：可以用于执行任何SQL语句，一般用于执行DDL语句；  
update方法及batchUpdate方法：update方法用于执行新增、修改、删除等语句；batchUpdate方法用于执行批处理相关语句；  
query方法及queryForXXX方法：用于执行查询相关语句；  
call方法：用于执行存储过程、函数相关语句。
 
 打开mysql的批处理(将其添加到url中)：

> rewriteBatchedStatements=true

> addBatch()
> executeBatch()

