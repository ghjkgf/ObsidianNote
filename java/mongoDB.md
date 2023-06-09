![[Pasted image 20230129131108.png]]

-   **admin**： 从权限的角度来看，这是"root"数据库。要是将一个用户添加到这个数据库，这个用户自动继承所有数据库的权限。一些特定的服务器端命令也只能从这个数据库运行，比如列出所有的数据库或者关闭服务器。
-   **local:** 这个数据永远不会被复制，可以用来存储限于本地单台服务器的任意集合
-   **config**: 当Mongo用于分片设置时，config数据库在内部使用，用于保存分片的相关信息。

### document 
	文档是一组键值(key-value)对(即 BSON)。MongoDB 的文档不需要设置相同的字段，并且相同的字段不需要相同的数据类型

1.  文档中的键/值对是有序的。
2.  文档中的值不仅可以是在双引号里面的字符串，还可以是其他几种数据类型（甚至可以是整个嵌入的文档)。
3.  MongoDB区分类型和大小写。
4.  MongoDB的文档不能有重复的键。
5.  文档的键是字符串。除了少数例外情况，键可以使用任意UTF-8字符。
	-   键不能含有`\0` (空字符)。这个字符用来表示键的结尾。
	-   .和$有特别的意义，只有在特定环境下才能使用。
	-   以下划线"_"开头的键是保留的(不是严格要求的)。

### collection
集合就是 MongoDB 文档组,可以将不同数据结构的文档插入到集合中
-   集合名不能是空字符串""。
-   集合名不能含有`\0`字符（空字符)，这个字符表示集合名的结尾。
-   集合名不能以"system."开头，这是为系统集合保留的前缀。
-   用户创建的集合名字不能含有保留字符。有些驱动程序的确支持在集合名里面包含，这是因为某些系统生成的集合中包含该字符。除非你要访问这种系统创建的集合，否则千万不要在名字里出现$。

### capped collections

Capped collections 就是固定大小的collection。
	capped 加盖子的,->有限制的
它有很高的性能以及==队列过期==的特性(过期按照插入的顺序). 有点和 "RRD" 概念类似。[RRDtool - About RRDtool (oetiker.ch)](https://oss.oetiker.ch/rrdtool/)

Capped collections 是高性能自动的维护对象的插入顺序。它非常适合类似记录日志的功能和标准的 collection 不同，你必须要显式的创建一个capped collection，指定一个 collection 的大小，单位是字节。

Capped collections 可以按照文档的插入顺序保存到集合中，而且这些文档在磁盘上存放位置也是按照插入顺序来保存的，所以当我们更新Capped collections 中文档的时候，更新后的文档不可以超过之前文档的大小，这样话就可以确保所有文档在磁盘上的位置一直保持不变。

由于 Capped collection 是按照文档的插入顺序而不是使用索引确定插入位置，这样的话可以提高增添数据的效率。MongoDB 的操作日志文件 oplog.rs 就是利用 Capped Collection 来实现的。

要注意的是指定的存储大小包含了数据库的头信息。

db.createCollection("mycoll", {capped:true, size:100000})

-   在 capped collection 中，你能添加新的对象。
-   能进行更新，然而，对象不会增加存储空间。如果增加，更新就会失败 。
-   使用 Capped Collection 不能删除一个文档，可以使用 drop() 方法删除 collection 所有的行。
-   删除之后，你必须显式的重新创建这个 collection。
-   在32bit机器中，capped collection 最大存储为 1e9( 1X109)个字节。


### 元数据

数据库的信息是存储在集合中。它们使用了系统的命名空间：

dbname.system.*

在MongoDB数据库中名字空间 `<dbname>.system.*` 是包含多种系统信息的特殊集合(Collection)，如下:

集合命名空间 | 描述
--- | ---
dbname.system.namespaces | 列出所有名字空间。
dbname.system.indexes | 列出所有索引。
dbname.system.profile | 包含数据库概要(profile)信息。
dbname.system.users | 列出所有可访问数据库的用户。
dbname.local.sources | 包含复制对端（slave）的服务器信息和状态。

对于修改系统集合中的对象有如下限制。

在{{system.indexes}}插入数据，可以创建索引。但除此之外该表信息是不可变的(特殊的drop index命令将自动更新相关信息)。

{{system.users}}是可修改的。 {{system.profile}}是可删除的.

### 数据类型

![[Pasted image 20230129140001.png]]
### ObjectId

ObjectId 类似唯一主键，可以很快的去生成和排序，包含 12 bytes，含义是：

-   前 4 个字节表示创建 **unix** 时间戳,格林尼治时间 **UTC** 时间，比北京时间晚了 8 个小时
-   接下来的 3 个字节是机器标识码
-   紧接的两个字节由进程 id 组成 PID
-   最后三个字节是随机数
- ![[Pasted image 20230129141235.png]]

### 字符串

**BSON 字符串都是 UTF-8 编码。**

### 时间戳

BSON 有一个特殊的时间戳类型用于 MongoDB 内部使用，与普通的 日期 类型不相关。 时间戳值是一个 64 位的值。其中：

-   前32位是一个 time_t 值（与Unix新纪元相差的秒数）
-   后32位是在某秒中操作的一个递增的`序数`

在单个 mongod 实例中，时间戳值通常是唯一的。

在复制集中， oplog 有一个 ts 字段。这个字段中的值使用BSON时间戳表示了操作时间。

> BSON 时间戳类型主要用于 MongoDB 内部使用。在大多数情况下的应用开发中，你可以使用 BSON 日期类型。

### 日期

表示当前距离 Unix新纪元（1970年1月1日）的毫秒数。日期类型是有符号的, 负数表示 1970 年之前的日期。
```js
> var mydate1 = new Date()     //格林尼治时间
> mydate1
ISODate("2018-03-04T14:58:51.233Z")
> typeof mydate1
object

> var mydate2 = ISODate() //格林尼治时间
> mydate2
ISODate("2018-03-04T15:00:45.479Z")
> typeof mydate2
object

这样创建的时间是日期类型，可以使用 JS 中的 Date 类型的方法。

返回一个时间类型的字符串：

> var mydate1str = mydate1.toString()
> mydate1str
Sun Mar 04 2018 14:58:51 GMT+0000 (UTC) 
> typeof mydate1str
string

或者

> Date()
Sun Mar 04 2018 15:02:59 GMT+0000 (UTC)

```

-   WriteConcern.NONE:没有异常抛出
-   WriteConcern.NORMAL:仅抛出网络错误异常，没有服务器错误异常
-   WriteConcern.SAFE:抛出网络错误异常、服务器错误异常；并等待服务器完成写操作。
-   WriteConcern.MAJORITY: 抛出网络错误异常、服务器错误异常；并等待一个主服务器完成写操作。
-   WriteConcern.FSYNC_SAFE: 抛出网络错误异常、服务器错误异常；写操作等待服务器将数据刷新到磁盘。
-   WriteConcern.JOURNAL_SAFE:抛出网络错误异常、服务器错误异常；写操作等待服务器提交到磁盘的日志文件。
-   WriteConcern.REPLICAS_SAFE:抛出网络错误异常、服务器错误异常；等待至少2台服务器完成写操作。

查询操作符
投影操作符
![[Pasted image 20230129235933.png]]
使用$type时的码表.

![[Pasted image 20230130002132.png]]

### 副本集特征：

-   N 个节点的集群
-   任何节点可作为主节点
-   所有写入操作都在主节点上
-   自动故障转移
-   自动恢复

需要自己搭一个主从看看效果https://www.runoob.com/mongodb/mongodb-replication.html

覆盖索引查询是以下的查询： 
-   所有的查询字段是索引的一部分
-   所有的查询返回字段在同一个索引中

https://developer.aliyun.com/article/798758    explain

**regex操作符的介绍**

MongoDB使用$regex操作符来设置匹配字符串的正则表达式，使用PCRE(Pert Compatible Regular Expression)作为正则表达式语言。

-   regex操作符
    -   {<field>:{$regex:/pattern/，$options:’<options>’}}
    -   {<field>:{$regex:’pattern’，$options:’<options>’}}
    -   {<field>:{$regex:/pattern/<options>}}

-   正则表达式对象
    -   {<field>: /pattern/<options>}

$regex与正则表达式对象的区别:

-   在$in操作符中只能使用正则表达式对象，例如:{name:{$in:[/^joe/i,/^jack/}}
-   在使用隐式的$and操作符中，只能使用$regex，例如:{name:{$regex:/^jo/i, $nin:['john']}}
-   当option选项中包含X或S选项时，只能使用$regex，例如:{name:{$regex:/m.*line/,$options:"si"}}

**$regex操作符的使用**

$regex操作符中的option选项可以改变正则匹配的默认行为，它包括i, m, x以及S四个选项，其含义如下

-   i 忽略大小写，{<field>{$regex/pattern/i}}，设置i选项后，模式中的字母会进行大小写不敏感匹配。
-   m 多行匹配模式，{<field>{$regex/pattern/,$options:'m'}，m选项会更改^和$元字符的默认行为，分别使用与行的开头和结尾匹配，而不是与输入字符串的开头和结尾匹配。
-   x 忽略非转义的空白字符，{<field>:{$regex:/pattern/,$options:'m'}，设置x选项后，正则表达式中的非转义的空白字符将被忽略，同时井号(#)被解释为注释的开头注，只能显式位于option选项中。
-   s 单行匹配模式{<field>:{$regex:/pattern/,$options:'s'}，设置s选项后，会改变模式中的点号(.)元字符的默认行为，它会匹配所有字符，包括换行符(\n)，只能显式位于option选项中。

使用$regex操作符时，需要注意下面几个问题:

-   i，m，x，s可以组合使用，例如:{name:{$regex:/j*k/,$options:"si"}}
-   在设置索弓}的字段上进行正则匹配可以提高查询速度，而且当正则表达式使用的是前缀表达式时，查询速度会进一步提高，例如:{name:{$regex: /^joe/}