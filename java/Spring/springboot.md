SpringApplication做的4件事情
- 推断是否为web项目
- 查找并加载所有可用初始化器,设置到initializers属性中
- 找出所有应用程序监听器,设置到listeners属性中
- 推断并设置main方法的定义类,找到运行的主类