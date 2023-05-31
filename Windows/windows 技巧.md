### 关闭win键

#### Windows禁用特定键盘快捷键

其实只需简单调整下注册表，就可以禁用 Windows 7/8/10 中任意特定 Win + 键盘组合。

1 使用 Windows + R 快捷键打开「运行」——执行 regedit 打开注册表编辑器

2 导航到如下路径：

复制计算机\\HKEY\_CURRENT\_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\Advanced

3 右击新建一个名为 DisabledHotkeys 的「字符串值」

![](https://img.sysgeek.cn/img/2018/05/disable-windows-keyboard-shortcut-2.jpg)

如果你希望禁用 Win + S 快捷键，只需在值中写入 S 即可。如果还想禁用其它特定键盘快捷键如 Win + X，再在值中加写上 X。以此类推，把需要禁用的值**全写到** DisabledHotkeys 里面就成。

![DisabledHotkeys](https://img.sysgeek.cn/img/2018/05/disable-windows-keyboard-shortcut-3.jpg)

> 注册表改完后需要重启计算机或通过任务管理器重启 Explorer.exe 进程之后才能生效。

#### Windows禁用全部键盘快捷键

如果您嫌挨个去想再来禁用比较麻烦，可以通过编辑组策略来禁用全部快捷键。

1 使用 Windows + R 快捷键打开「运行」——执行 gpedit.msc 打开本地组策略编辑器

2 导航到如下路径：

用户配置——管理模板——Windows 组件——文件资源管理器

3 在右侧窗格中找到「关闭 Windows 键热键」这条策略，将其设置为「已启用」

![关闭 Windows 键热键](https://img.sysgeek.cn/img/2018/05/disable-windows-keyboard-shortcut-4.jpg)

4 组策略更改完成后可以使用 gpupdate /force 命令强制刷新或重启计算机让其生效。



### 壁纸位置

#### 锁屏壁纸
User\AppData\Local\Packages\Microsoft.Windows.ContentDeliveryManager_cw5n1h2txyewy\LocalState\Assets

### java
java -version和环境变量配的不一致,说是Oracle环境变量导致的,但是改变顺序后仍然无效.
java 环境变量含空格,会导致rocketMQ启动失败

### PIN码不可用
装新硬盘(maybe内存条)时,bios里的安全模块 TPP选项会自动关闭,需要手动开启