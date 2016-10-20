title: 设置“Everything”而让它调用外部文件管理器
categories: 办公工具
tags:
  - TC
  - 办公工具
  - 学习
id: 125
date: 2014-08-17 12:20:34
---

打开“Everything”安装文件夹中的Everything.ini文件。添加如下两行到文件末尾。
open_folder_command=$exec(“ExternalFileManager.exe” “%1″)
open_folder_path_command=$exec(“ExternalFileManager.exe” “$parent(%1)”)
请用完整的路径名和文件名替换上两行中的 ExternalFileManager.exe
-------------------------------------------------------------------
比如，
open_path_command=$exec(“d:\Program Files\tc\TOTALCMD.EXE” “$parent(%1)”)
open_folder_command=$exec(“d:\Program Files\tc\TOTALCMD.EXE” “%1″)

&nbsp;

## Everything 1.3.1.636b及此后版本，配置界面或修改ini文件，调用外部文件管理器

Everything 1.3.1.636b版本，已经可以通过配置界面进行修改，如图：
[pe2-image src="http://lh6.ggpht.com/-UEyVbYzr6mU/U_Ghknmy3JI/AAAAAAAAAbo/YfVnhRi70Ko/s144-c-o/veve.jpg" href="https://picasaweb.google.com/111994961921407437567/RvJMSG#6048793425014348946" caption="" type="image" alt="veve.jpg" ]

open_folder_command2=open_folder_command2=$exec("d:\资源管理\TOTALCMD64.EXE" "%1")

配置结果记录在ini文件中。为了避免与旧版冲突，配置后的结果记录于新参数（原参数后面加2）。当然，你也可以直接修改ini文件，得到同样的效果。

open_path_command**2**=$exec(“d:\Program Files\tc\TOTALCMD.EXE” “$parent(%1)”)

open_folder_command**2**=$exec(“d:\Program Files\tc\TOTALCMD.EXE” “%1″)