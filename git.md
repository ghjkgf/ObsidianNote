git config --global http.sslVerify "false"    解决10054的问题

git clone 'url'      从远端克隆项目
设置代理/取消代理  解决访问不通的问题
git config --global https.proxy http://127.0.0.1:1080
git config --global https.proxy https://127.0.0.1:1080
git config --global http.proxy 'socks5://127.0.0.1:1080' 
git config --global https.proxy 'socks5://127.0.0.1:1080'
git config --global --unset http.proxy  
git config --global --unset https.proxy

忘记fork直接从github拉取项目后无法commit and push
https://blog.csdn.net/u010299133/article/details/88967476
 1. git add .
 2. git commit 
 3. git remote rm origin
 4. git remote add origin URL
 5. git remote -V
 6. git push -u OldBranchName NewBranchName
 

1、创建账号　

1

2

`git config --global user.name` `"anyijmxsy1"`

`git config --global user.email` `"737653@qq.com"`

2、进入本地项目文件中，初始化

1

`git init`

3、提交本地代码

1

2

3

`git add .`

`git commit -m` `"first commit"`

4、查看文件修改情况

1

`git status`

5、查看具体的内容修改

1

`git diff`

6、在提交之前(未使用add命令前），撤销修改

1

2

3

`git checkout`

`git checkout app/src/main/java/com/example/providertest/mainActivity.java`

7、查看历史提交信息

1

`git log`

8、创建分支并切换到分支上

1

2

3

`git branch version1.``0`

`git checkout version1.``0`

9、将分支修改的内容合并到主干上

1

2

3

`git checkout master`

`git merge version1.``0`

10、将远程代码下载到本地，粘贴操作shift + insert

1

`git clone https:``//github.com/example/test.git`

11、将本地代码上传到远程版本库

1

2

3

4

5

`git push origin master`

`//或者将分支上传`

`git push origin version1.``0`

11、将远程版本库上获取最新修改的代码下载并合并到本地

1

`git pull origin master`

12、查看本地文件

1

`ls -al`


idea里使用git,可以直接拖拽文件,等效于git mv 命令
重命名一样

has no tracked branch
3个模块,导致的问题
新拉分支后,push时取消勾选 另外两个模块,切换到dev时,另外两个要手动checkout 到master

github功能
[你可能不知道的15个有用的Github功能-华为开发者论坛 | 华为开发者联盟 (huawei.com)](https://developer.huawei.com/consumer/cn/forum/topic/0201403843309700193)

