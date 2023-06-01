这里提供两种方式：

一、第一种：不能保存会话信息，即每次连接都要重新输入一遍

1 Tools→Start [SSH](https://so.csdn.net/so/search?q=SSH&spm=1001.2101.3001.7020) session...

![](https://img-blog.csdnimg.cn/20190120212138168.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3d1Z2VucWlhbmc=,size_16,color_FFFFFF,t_70)

2 选择Edit credentials...

![](https://img-blog.csdnimg.cn/20190120212251153.png)

3 输入SSH登录信息即可

![](https://img-blog.csdnimg.cn/20190120212349539.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3d1Z2VucWlhbmc=,size_16,color_FFFFFF,t_70)

4 连接成功~~

![](https://img-blog.csdnimg.cn/20190120212416281.png)

![](https://img-blog.csdnimg.cn/2019012021243521.png)

二、第二种：可以保存会话信息

1  Tools → Deployment →[Configuration](https://so.csdn.net/so/search?q=Configuration&spm=1001.2101.3001.7020)

![](https://img-blog.csdnimg.cn/20190121110254796.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3d1Z2VucWlhbmc=,size_16,color_FFFFFF,t_70)

2 点击左上角+号，选中SFTP，填写名字

![](https://img-blog.csdnimg.cn/201901211107138.png)

![](https://img-blog.csdnimg.cn/20190121110851137.png)

3 然后开始输入host、port、name和密码，可以点击 Test SFTP connection测试连接

![](https://img-blog.csdnimg.cn/20190121111047536.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3d1Z2VucWlhbmc=,size_16,color_FFFFFF,t_70)

点击save password，最后点击ok即可

4 验证是否可以下次可直接登入

Tools →  Start SSH [Session](https://so.csdn.net/so/search?q=Session&spm=1001.2101.3001.7020) → 就会出现刚才命名的会话，选择即可

![](https://img-blog.csdnimg.cn/20190121111403727.png)

![](https://img-blog.csdnimg.cn/20190121111616379.png)