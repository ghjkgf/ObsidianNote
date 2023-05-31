## **Windows 10可选功能**

这个列表里面功能项这么多，哪些是可以关掉的 Windows 10 可选功能呢？Windows 10 企业版功能最多，下面我们以 Windows 10 企业版为例，把常用功能给大家介绍一下。

-   **.NET Framework 3.5 (包括 .NET 2.0 and 3.0)**：该功能是用于运行 .NET 程序的运行时，建议默认状态。在未启用状态下，首次执行需要它的 .NET 程序时，Windows 会自动安装并启用。
-   **.NET Framework 4.6 高级服务**：如果应用程序需要也会自动安装，建议默认状态。
-   **Active Directory 轻型目录服务**：提供 LDAP （轻量级目录访问协议）服务器，它会作为 Windows 服务运行并提供代替完整 Active Directory 进行目录验证的工作，普通用户一般关闭。
-   **Hyper-V**：微软的 [Hyper-V](https://link.zhihu.com/?target=http%3A//www.sysgeek.cn/enable-windows-10-client-hyper-v/) 虚拟化工具，它包括基础平台和服务，可用于创建、管理和使用图形化的 Hyper-V 管理工具。
-   **Internet Explorer 11**：这个没啥好说的，就是传统的 IE 浏览器。如果你不使用 Internet Explorer 11，可以取消勾选将其完全禁用掉。
-   **Internet Information Services**：提供微软的 IIS 和 FTP 服务，除开发测试之外，一般很少在 Windows 客户端上安装使用。
-   **Internet Information Services 可承载的 Web 核心**：允许应用程序在自己的进程内来承载使用 IIS 的 web 服务器，普通用户用不上。
-   **隔离用户模式**：Windows 10 中的新功能，允许应用程序在一个安全、独立的空间中执行。[该视频](https://link.zhihu.com/?target=https%3A//channel9.msdn.com/Blogs/Seth-Juarez/Isolated-User-Mode-in-Windows-10-with-Dave-Probert)提供了此功能的各种细节。
-   **旧版组件 (DirectPlay)**：DirectPlay 是 DirectX 的一部分，可用于游戏组网进行多人游戏。当你使用的游戏需要用到 DirectPlay 功能时，Windows 10 会自动进行安装，默认关闭。
-   **媒体功能 (Windows Media Player)**：选择是否启用 Windows Media Player，现在像 [PotPlayer](https://link.zhihu.com/?target=http%3A//www.sysgeek.cn/potplayer-bluescreen/) 一样强大的媒体播放器这么多，相信没多少人用它了吧。默认启用。
-   **Microsoft Message Queue (MSMO) 服务器**：用于提高不可靠网络通信的老版消息队列服务器，普通用户用不上。默认禁用。
-   **Microsoft Print to PDF**：Windows 10 内置的[将文档打印成 PDF](https://link.zhihu.com/?target=http%3A//www.sysgeek.cn/create-pdf-windows-10/) 的虚拟打印机。
-   **MultiPoint Connector**：允许 MultiPoint Manager 对计算机进行监控和管理的组件，只对使用 MultiPoint Manager 的企业网络有用。默认禁用。
-   **打印和文件服务**：其中的「Internet 打印客户端」和「Windows 传真和扫描」功能默认启用，在此选项中还可以添加老旧的 LPD 和 LPR 网络打印协议。如果你需要使用网络打印机，则需要启用「Internet 打印客户端」。
-   **RAS 连接管理器管理工具包（CMAK）**：此工具用户创建定制的 VPN 远程访问配置文件，一般不启用。默认关闭。
-   **远程差分压缩 API 支持**：该组件为「需要的」应用程序提供了文件快速同步算法，默认启用。
-   **RIP 侦听器**：该服务用于侦听路由器发送的路由信息协议公告，只用于支持 RIPv1 协议的路由器。默认关闭。
-   **简单网络管理协议（SNMP）**：用于管理路由器、交换机和其它网络设备的旧协议，也被用于系统资源监控。默认关闭。
-   **简单 TCPIP 服务（即echo、daytime等）**：该功能组件包括一些可选的网络服务，如进行网络故障诊断的「echo」服务等。普通用户无用，默认关闭。
-   **SMB 1.0/CIFS 文件共享支持**：该服务主要为旧版 Windows 如 Windows NT 4.0 到 Windows XP 和 Windows Server 2003 R2 及 Linux 和 Mac 提供较旧的 SMB 共享协议支持。
-   **Telnet 客户端**：提供连接到远程 Telnet 服务器设备的客户端支持，虽然 Telnet 协议不安全，但在连接老旧设备时还是非常有用。可选启用，默认关闭。
-   **TFTP 客户端**：提供 tftp 命令行客户端支持，不安全，不建议使用。默认关闭。
-   **Windows Identity Foundation 3.5**：.NET 4 中已经包括了一个新的框架，但如果使用旧的 .NET 应用程序仍然可能需要安装它。默认关闭。
-   **Windows PowerShell 2.0**：PowerShell 是 Windows 中的高级脚本和命令行环境，默认启用，不建议关闭。
-   **Windows Process Activation Service**：该选项与 IIS 的 Web 服务有关，如果应用程序服务需要再启用。默认关闭。
-   **Windows Subsystem for Linux**：Windows 10 周年更新中的一个新功能，开启      [Bash on ubuntu on Windows](https://link.zhihu.com/?target=http%3A//www.sysgeek.cn/enable-bash-on-ubuntu-on-windows/) 之后可以支持在 Windows 10 中原生支持 [Bash Shell](https://link.zhihu.com/?target=http%3A//www.sysgeek.cn/tag/linux-shell/)。
-   **Windows TIFF iFilter**：该功能使用 Windows 索引服务来分析 TIFF 文件和进行光学字符识别（OCR），默认禁用。
-   **工作文件夹客户端**：该选项是 Work Folders 功能的客户端组件，可以让你与公司文件服务器进行同步。默认启用。
-   **XPS 服务**：将文件打印成 XPS 文档功能，Windows Vista 开始支持微软独有的 XPS 文件格式，不过目前还是 PDF 为主流。默认启用。
-   **XPS 查看器**：XPS 文件查看工具。默认启用

