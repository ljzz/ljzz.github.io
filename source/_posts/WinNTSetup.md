title: 系统安装器 WinNTSetup v3.7.0 汉化绿色版
categories: 系统工具
tags:
  - ESD
  - PE
  - win7
  - win8
  - 便携绿色
  - 安装
  - 操作系统
  - 系统工具
id: 340
date: 2014-10-22 09:02:09
---

WinNTSetup 是一款功能非常强大的系统安装器，可以直接从 Windows 平台或者 PE 环境下运行它来安装 MSDN 原版系统，从硬盘环境下直接安装微软操作系统的方法被称为硬盘安装法，这款工具的诞生以及更新为这一方法提供了诸多捷径，使用 WinNTSetup 您只需要定位好待安装系统文件的位置以及安装目标路径即可。

WinNTSetup 还允许你在安装系统前对目标系统进行一些使用习惯方面的简单部署，比如：添加硬件驱动、破解第三方主题、添加无人值守、禁用系统还原、禁用虚拟内存页面文件等等。

当然你还可以勾选执行“禁用用户帐户控制、显示隐藏文件和文件夹、右键菜单显示“命令提示符”、删除快捷方式小箭头”等个性化操作，省去了系统安装完成后再次设置的麻烦。

预览图：

![](http://szcxgg.qiniudn.com/WinNTSetup.jpg)

功能&amp;特点：

支持安装 Win2k/XP/2k3/Vista/7/8/8.1/x86/x64 等；
即使在最精简的 WinPE 实际上也可运行；
支持选择新的 Windows 安装能驱动器盘符；
支持比如：nlite/vlite 已删除 winnt32.exe/setup.exe 安装 Windows；
集成驱动程序：正常 PNP 和文本模式的驱动程序也支持；
破解主题 uxtheme.dll 以支持第三方主题；
支持对系统的一些优化调整；
支持无人值守；
支持从低版本直到 Windows 8 和更高操作系统版本；
操作说明：

一、驱动程序安装

NT6.x 窗口中添加的每个驱动程序会添加到驱动程序存储区中。所以不建议添加了过多的驱动程序，但是可以添加真正需要的驱动。

二、无人值守安装选项：

它是可以使用 unattend.xml 来运行无人值守的安装程序。但由于实际 WinPE 安装阶段不是有效的安装方式，所有 WinPE 都相关设置里面 unattend.xml 不会被应用。

三、ini 配置文件

可以将所有的图形用户界面设置保存到一个 ini 文件：按 Ctrl + S 保存所有的设置到 ini。按 Ctrl + L 从 ini 加载所有设置。作为应用程序本身的相同目录中的 WinNTSetup.ini 文件将会在启动时自动加载。它还可以通过命令行进行选择：WinNTSetup.exe”/configfile:”C:\mysettings.ini。

四、若要安装 Windows 中一个 VHD 文件

需要 Windows 7 操作系统与 Windows 7 旗舰版，企业或作为源服务器 2008 R2 ；
创建分区的 VHD 并指派一个驱动器号（按 Ctrl + Shift + V，使用生成在 diskpart 安装为此驱动器）；
选择 VHD 驱动器作为安装驱动器（确保您启动上的物理磁盘驱动器是一个活动的主分区）；
如果您从您的防病毒软件获取防病毒的警告（比如：大数字误报），请添加信任即可！

WinNTSetup v3.7.0 更新日志：

- 新增对 Windows 10（Windows Threshold）环境运行兼容性的支持；

WinNTSetup v3.6.5 更新日志：

- 修正 syspreped WinXP 离线注册表错误的问题；
- 修正关于对话框 DPI 问题；
- 如果 WIM 中 index 名字和显示名未定义将使用 XML 描述字段；
- 如果注册表加载失败，将记录离线日志错误代码和注册表 hive 路径；
- 引导项现在包含（WIMBOOT）或）VHDX）如果使用这些选项；
- WinNTSetup_iso 移动 tool 文件夹中；

[下载地址](http://pan.baidu.com/s/1hq1P812)