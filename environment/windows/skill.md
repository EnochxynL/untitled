
```bash
winget install --accept-package-agreements --source msstore --name "WPS Office X64"
winget install --accept-package-agreements --source msstore --name "QQ桌面版"
winget install --accept-package-agreements --source msstore --name "腾讯会议"
winget install --accept-package-agreements --source msstore --name "金山文档"
winget install --accept-package-agreements --source msstore --name "腾讯文档"
winget install --accept-package-agreements --source msstore --name "网易云音乐"
winget install --accept-package-agreements --source msstore --name "夸克网盘"
winget install --accept-package-agreements --source msstore --name "夸克"
winget install --accept-package-agreements --source msstore --name "迅雷12"
winget install --accept-package-agreements --source msstore --name "百度翻译-轻快多语种"
winget install --source msstore --name "百度网盘"
winget install --source msstore --name "微信"
```

# 认识系统

## 认识Windows精简版

[Windows 精简大神俄罗斯网友 lopatkin 新网址来了 发布新中文pip版 - Windows - 远景论坛 - 前沿科技与智慧生态的极客社区 -](https://bbs.pcbeta.com/viewthread-1632178-1-1.html)  
[俄大神系统精简版对比-CSDN博客](https://blog.csdn.net/Tifa_Best/article/details/87902280)

[lopatkin俄大神精简中文系统 DREY PIP MICRO BOX LITE区别-CSDN博客](https://blog.csdn.net/chengtan3348/article/details/100785381)

[版本说明-百度贴吧](https://tieba.baidu.com/p/6177207341)

[大神系统各版本的区别-百度贴吧](https://tieba.baidu.com/p/5439809486)

[4月 Win10企业版 1803 64位PIP BOX LIM-百度贴吧](https://tieba.baidu.com/p/5645463307)

[Windows-IOSFiles/Lopatkin.md at master · 2144291529/Windows-IOSFiles](https://github.com/2144291529/Windows-IOSFiles/blob/master/Lopatkin.md)

[哪位大神清楚lopatkin系统DREY、PIP、LITE、MINI、SM、SMS的含义？ - 综合讨论区 - 无忧启动论坛 - Powered by Discuz!](http://wuyou.net/forum.php?mod=viewthread&tid=420839)

[来一起加速：lopatkin最新2016LTSB_LIM+PIP2合一 - 远景论坛 - 前沿科技与智慧生态的极客社区 -](https://bbs.pcbeta.com/viewthread-1775513-1-1.html)

[问下俄大神lopatkin系统里的PIP和LIM有啥区别？-百度贴吧](https://tieba.baidu.com/p/9184925947)

[Win10俄大神精简版与官方精简版与官方原版区别介绍 - 哔哩哔哩](https://www.bilibili.com/opus/407051793158564114)

[俄罗斯大神win7精简版_俄罗斯大神精简版Windows系统镜像合集（内附Onedrive恢复方法）...-CSDN博客](https://blog.csdn.net/weixin_39902870/article/details/110361280)

传奇精简系统，Windows 10能装进12G傲腾盘

## 可选：完整迁移用户目录

[Windows系统更改/迁移用户目录 - Macrored - 博客园](https://www.cnblogs.com/macrored/p/15849185.html)

[改变 Windows 用户文件夹默认路径 C:/Users_修改users默认路径-CSDN博客](https://blog.csdn.net/weixin_51204324/article/details/132555913)

# 包管理器

[Windows 上最好的包管理工具是 Chocolatey 还是 Scoop ？ - 知乎](https://www.zhihu.com/question/369403302?sort=created)

[/转/ Windows命令行软件安装服务比较：Chocolatey、Scoop 与 winget - 知乎](https://zhuanlan.zhihu.com/p/694665774)

重装Windows 10应用商店：[重装Win10应用商店 - 知乎](https://zhuanlan.zhihu.com/p/618916095)，下载 [Reinstall-preinstalledApps.zip](https://link.zhihu.com/?target=http%3A//go.microsoft.com/fwlink/%3FLinkId%3D619547) 文件

1. 生活用`msstore`（包括工具链的启动器）。只要能在微软应用商店安装，就在应用商店安装，便于管理。
2. 生产用`winget/msi/exe`（工具链、VSCode）软件，或无法在应用商店找到的软件，用安装器安装，且用管理员模式以免装进AppData难以查找，winget可以自然发现，因此exe直接安装。
3. 绿色小工具用`scoop`。没有安装包，或使用脚本安装的绿色软件（如Maven），用scoop安装。scoop默认会存放在`C:\Users\enoch`中。

# 环境变量

我就用"D:\Users\enoch\Documents\WindowsPowerShell\profile.ps1”改环境变量，反正只是终端用，也不会污染Windows设置

# 推荐软件

Acrobat+MarkText+MarukoToolbox+VideoCaptioner

[(22 封私信 / 87 条消息) 管理桌面文件Easy File Organizer - 知乎](https://zhuanlan.zhihu.com/p/548906538)

Space Thumbnails已被F3D和Open 3D Model Viewer替代

PowerToys可以预览代码和Markdown

[Folder Size Explorer - Simple Windows Explorer with folder sizes.](https://www.folder-sizes-explorer.com/)  
[Folder Size Explorer - Simple Windows Explorer with folder sizes and more...](https://www.folder-size-explorer.com/index.shtml)  
[FolderSizes Feature Comparison](https://www.foldersizes.com/features)  
[Diskitude - Made by Evan](https://madebyevan.com/diskitude/)  
[SpaceSniffer官网下载 - 智能磁盘空间分析工具中文安装使用教程](https://www.spacesniffer.com.cn/)  
[SpaceSniffer download](https://www.uderzo.it/main_products/space_sniffer/download.html)  
[六大磁盘分析工具对比-CSDN博客](https://blog.csdn.net/qq_27898413/article/details/117248833)  
[WizTree - The Fastest Disk Space Analyzer](https://www.diskanalyzer.com/)  
[Free Disk Space Analyzer Software for Windows - FolderSizes](https://www.foldersizes.com/)

FolderSizes 9是功能最全的

[【教學】將BlueStacks模擬器的檔案複製到電腦，共用文件](https://www.pkstep.com/bluestacks-files-to-computer/)

res-downloader+XDM+qBittorrent

# 下载管理

[同比6款热门下载器，IDM还是最好用的那个吗？ - 知乎](https://zhuanlan.zhihu.com/p/500792340)

[视频号直播自动录制方案，使用RPA+快抖工具实现开播自动检测与录制_视频号直播监控录制-CSDN博客](https://blog.csdn.net/zzl1243976730/article/details/151967129)

[视频号直播录屏全攻略：两种方法轻松搞定 - 哔哩哔哩](https://www.bilibili.com/opus/1071279068282880069)

# 网络问题

## 多网卡Timeout问题

[window11 查看本地端口是否开放_win11查看3306端口是否开放-CSDN博客](https://blog.csdn.net/m0_50641264/article/details/128478466)

`A connection timeout has occurred while trying to connect to '172.27.240.1' on port '4000'. The issue could either be caused by a networking problem, by a firewall or NAT blocking incoming traffic or by a wrong server address. Please verify your configuration and try again.`

NoMachine有一个特性/安全漏洞，你可以发现局域网下其他设备的所有网络适配器的IP。而自动设置的IP所对应的网卡可能与本机网卡根本不在同一个局域网下。

打开目标机器的ipconfig，发现控制机器自动分配的172地址对应的是vEthernet而不是Wi-Fi，于是找到Wi-Fi对应的192地址，把控制机器的172换成192。