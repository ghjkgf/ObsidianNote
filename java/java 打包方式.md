exploded 分解的(没有压缩的)

artifact   [[maven]]中的概念,表示某个module如何打包

一个module有了 Artifacts 就可以部署到应用服务器中了

jar,war,ear,car
java/web/enterprise/webx archive file

jar是文件封装的最小单元
### WAR 

> **包含内容**：`Servlet`、`JSP页面`、`JSP标记库`、`JAR库文件、HTML/XML文档和`其他公用资源文件，如`图片、音频文件`等  
> **部署文件** ： web.xml  
> **容器**： 小型服务程序容器（servlet containers）  
> **级别**：中
### EAR

> **包含内容**：除了包含`JAR`、`WAR`以外，还包括`EJB组件`  
> **部署文件** ： application.xml  
> **容器**： EJB容器（EJB containers）  
> **级别**： 大

### car包(`webx特有的打包方式`)

> 传统的web工程就是将工程打包成一个war包部署到web服务器上就可以运行web服务。  
> Webx工程是以car包为单位，一个工程可以打包为一个car包，多个car包可以打包成一个war包部署到 web服务器上。  
> 这样做的好处不言而喻就是可以将一个大工程分解为多个小工程独立去开发部署。

