jetbrains软件都启动失败,报错 java.net.BindException: Address already in use: bind
https://blog.csdn.net/u011830577/article/details/112511145
https://github.com/docker/for-win/issues/3171#issuecomment-459205576
需要看下面这个
https://intellij-support.jetbrains.com/hc/en-us/community/posts/360004973960-Critical-Internal-Error-on-Startup-of-IntelliJ-IDEA-Cannot-Lock-System-Folders-
```shell
# 管理员powershell执行
Get-NetAdapter | Disable-NetAdapter -Confirm:$false -PassThru:$true | Enable-NetAdapter
```


idea64.exe.vmoptions文件里:
-Xms128m	初始堆大小
-Xmx750m 	最大堆大小

idea.properties文件

//修改注释语句颜色  
//ctrl+shift+数字     书签
//项目编码 editor->file encodings;右下角可以单独设置此项目的编码
//自动编译 	https://juejin.cn/post/6844904097808646151 	

//代码自动补全:光标不小心移动后,按alt+C

ctrl+alt+S  打开设置

[IntelliJ IDEA 的 20 个代码自动完成的特性](https://www.oschina.net/translate/top-20-code-completions-in-intellij-idea?cmp)

ctrl+shift+enter 自动补全结尾

ctrl+J :psvm,sout之类

ctrl+alt+l:格式化代码

ctrl+alt+i :自动缩进

ctrl+e:显示最近修改的代码

ctrl+p:方法参数提示

ctrl+alt+t:设置包围圈

ctrl+alt+m: 抽取代码块为新方法

ctrl+g :跳转到指定行

ctrl+w:选择,由小到大  加shift反向

ctrl+shift+u 转换大小写

alt+上下箭头:方法间跳跃

查找:
ctrl+n 查找类
ctrl+shift+n 查找文件

ctrl+alt+f  抽取为全局变量

live template:可以自己设置

file and code Templates

postfix completion

sdk 配置
分为idea,project,module三级

![[Pasted image 20210127121607.png]]
![[Pasted image 20210127121734.png]]

### 插件
generateallsetter
gototabs:
    实现代码tab快速切换
    安装插件后,在 Keymap (section Main menu -> Window -> Editor Tabs -> Go To Tabs 自行添加快捷键
maven Helper
    查看maven依赖冲突的问题
**1. Codota 代码智能提示插件**
**2. Key Promoter X 快捷键提示插件**
**3. CodeGlance 显示代码缩略图插件**
**8. SonarLint 代码质量检查插件**
**9. Save Actions 格式化代码插件**
**11. Grep Console 自定义控制台输出格式插件**
**13. Statistic 代码统计插件**
**12. MetricsReloaded 代码复杂度检查插件**
**14. Translation 翻译插件**
**15. gyro SpringBootTest运行单测,复用之前启动过的Spring容器
一些配置
**1. 优化导包配置**   auto import
**2. 取消tab页单行显示**   editor tabs
**3. 双斜杠注释改成紧跟代码头** editor>code style>Java>comment code
**4. 选中复制多行** Keymap 搜索 duplicate
    移除duplicate line or selection 的快捷键,添加到 duplicate entire lines 上
**5. 取消匹配大小写** code completion>Match case
**7. 创建文件时，自动生成作者和时间信息** file and code templates>include>file header 添加
```java
/**  
 * @author 33653  
 * @date ${DATE}  
 * @apiNote  
 */
```
**8 . 显示行号和方法分割线** editor>general>appearance


idea 能不能状态回滚,比如添加maven框架后恢复到没有maven时的状态

自动格式化   tools->actions on save -> reformat code

热部署 
    Build，Excution,Deployment -> Compiler ，确保勾选 Build project automatically

    ```xml
    <dependency>  
        <groupId>org.springframework.boot</groupId>  
        <artifactId>spring-boot-devtools</artifactId>  
        <optional>true</optional>  
    </dependency>
    ```

当Idea被强制关闭后，重启Idea启动服务出现端口占用的情况，因为Idea默认会监听服务的端口号，这时我们需要手动关闭被占用端口号以方便服务重启，具体如下：

1. 使用windows命令行查看占用的端口信息
netstat -aon | findstr 端口

2.根据PID找到对应的程序
tasklist | findstr PID

3.强制终止程序
taskkill /f /t /im java.exe
