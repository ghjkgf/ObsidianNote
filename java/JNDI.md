JNDI（Java Name Directory Interface）是为应用服务器（Tomcat）管理资源所设置的目录样式的唯一标识。（数据库、网页、文档等）

通俗的讲，JNDI不单单是用来连接数据库的，它是通过命名服务来找到数据库并返回数据库连接，当然JNDI还可以管理当前应用服务器上的其他资源，如网页，文件等，它用来连接数据库时和JDBC最大的区别就是它是通过应用服务器配置（如Tomcat）的配置文件context.xml来找数据库驱动的，其次就是[[JDBC]]连接能承受的同时请求数太低了，JNDI连接池连接与之相比会好很多。