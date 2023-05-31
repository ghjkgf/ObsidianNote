### 正常模式
也可以删除字符
	h,j,k,l键分别对应左，下，上，右
	dtx 删除光标到x字符前,x保留
	
### 插入模式
i/a进入插入模式

### 命令模式
: 进入命令模式

### 可视模式
v 进入 可视模式

三种方法保存退出
- 编辑完文件，先按ESC，然后 : wq
- 编辑完文件，先按ESC，然后 : x
- 编辑完文件，先按ESC，然后 ZZ
:q! 放弃并退出
:q 未修改直接退出
:e! 放弃所有修改，并打开原来文件。
修改 ~/.vimrc 文件,将ESC键映射为两次j键                                       
inoremap jj <Esc>

vim 键位图 https://www.runoob.com/w3cnote/all-vim-cheatsheat.html