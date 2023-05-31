[maven全局配置文件settings.xml详解](https://www.cnblogs.com/jingmoxukong/p/6050172.html)


https://www.cnblogs.com/youzhibing/p/5427130.html


![[Pasted image 20210127132522.png]]
![[Pasted image 20210127124812.png]]
```
1.<localRepository>路径</localRepository>

2.<mirror>

         <id>nexus-aliyun</id>

         <mirrorOf>central</mirrorOf>

         <name>Nexus aliyun</name>

         <url>http://maven.aliyun.com/nexus/content/groups/public</url>

     </mirror>

3.<profile>

        <id>jdk-1.8</id>

        <activation>

            <activeByDefault>true</activeByDefault>

            <jdk>1.8</jdk>

        </activation>

        <properties>

            <maven.compiler.source>1.8</maven.compiler.source>

            <maven-compiler.target>1.8</maven-compiler.target>

            <maven-compiler.compilerVersion>1.8</maven-compiler.compilerVersion>

        </properties>

    </profile>
```

###### javaweb的maven:

1.pom.xml里增加<packaging>war<packaging>

2.
![[Pasted image 20210127124719.png]]

@5,如果没有自动生成web.xml;

@6,7,编辑web目录所在位置

3.配置tomcat
	

	
	
archetype:quickstart
	groupid:
	artifactid:
	
maven 打包
手动标注目录类型
创建resources资源文件夹
	创建,读取properties文件
	
	module间依赖:(同时设置)
		1.setting里
		2.pom文件里


maven-archetype-webapp:
	
**Artifact**  
这个有点不好解释，大致说就是一个项目将要产生的文件，可以是jar文件，源文件，二进制文件，war文件，甚至是pom文件。每个artifact都由groupId:artifactId:version组成的标识符唯一识别。需要被使用(依赖)的artifact都要放在仓库中
	
	
	对于自己的项目完成后可以通过 **mvn install** 命令将项目放到仓库中
	
	