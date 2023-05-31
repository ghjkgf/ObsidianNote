https://www.jianshu.com/p/da49f71b9fc8

restart.sh
``` shell
#!/bin/sh		
ps -ef|grep java|grep PermSize=512m|awk '{print $2}'|xargs kill -9
sleep 3
cd /home/weblogic/bea/user_projects/domains/mydomain
nohup sh bin/startWebLogic.sh > nohup.out 2>error.out&
```
#:用于单行注释
#! 约定标记,告诉系统这个脚本需要什么样的解释器来执行

ps : process status
