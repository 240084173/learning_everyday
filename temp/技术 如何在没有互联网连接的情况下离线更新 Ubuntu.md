# 技术|如何在没有互联网连接的情况下离线更新 Ubuntu
 技术|如何在没有互联网连接的情况下离线更新 Ubuntu            

*   [Linux 中国](/)
*   [技术](https://linux.cn/tech/)
*   [新闻](https://linux.cn/news/)
*   [观点](https://linux.cn/talk/)
*   [分享](https://linux.cn/share/)
*   [LCTT](/lctt/)

*   [桌面应用](https://linux.cn/tech/desktop/)
*   [系统运维](https://linux.cn/tech/sa/)
*   [软件开发](https://linux.cn/tech/program/)
*   [树莓派](https://linux.cn/tech/raspberrypi/)
*   [容器与云](https://linux.cn/tech/container/)
*   [区块链](https://linux.cn/portal.php?mod=list&catid=27)

*   [硬核观察](https://linux.cn/news/express/)

*   [极客漫画](https://linux.cn/talk/comic/)
*   [开源智慧](https://linux.cn/talk/ossip/)
*   [穿山甲专访](https://linux.cn/talk/interview/)
*   [开源之道](https://linux.cn/talk/ocselected/)
*   [代码英雄](https://linux.cn/talk/clh/)

*   [Linux 发行版](https://linux.cn/share/distro/)

    
|  |  | [文章](javascript:;) | **搜索** | 

 |

❏ 站外平台：

 文本模式

  

*   [文章](javascript:;)

如何在没有互联网连接的情况下离线更新 Ubuntu
=========================

作者： [Arindam](https://www.debugpoint.com/how-to-update-or-upgrade-ubuntu-offline-without-internet/) 译者： [LCTT](https://linux.cn/lctt/) [littlebirdnest](/lctt/littlebirdnest)

| 2022-11-14 23:29      

> 本指南介绍了如何在没有互联网连接的情况下离线更新 Ubuntu 的步骤。

在很多情况下，你可能需要在没有互联网连接的情况下更新你的 Ubuntu 系统。你可能在外地不方便上网，也可能你需要更新一堆未联网的 Ubuntu，不管是哪种情况，保持你的系统更新最新的软件包总是需要的。

当然，始终建议通过联网来更新系统。

但有时，出于安全考虑，这是不行的。连接到互联网可能需要给你的系统进行额外的加固，以保护它们免受黑客和恶意软件的攻击。

以下的方法使用 [apt-offline](https://github.com/rickysarraf/apt-offline) 来解决这些问题，并概述了在没有互联网的情况下离线更新 Ubuntu 的步骤。

### 准备环节

*   一台能连接到网络的 Ubuntu（你朋友的、咖啡馆、实验室系统）
*   存储了软件包的 U 盘
*   两个系统都安装了 `apt-offline`：一个系统离线，另一个系统联网

### 安装 apt-offline

在两个系统下安装 `apt-offline`。你可以使用以下命令安装：

```


1.  `sudo apt install apt-offline`


```

如果你想在离线的目标系统安装 `apt-offline`，你可以提前下载到 U 盘里，然后复制到目标系统，再使用下面的命令安装。

Ubuntu 22.04 LTS 和其他版本的下载链接如下所示。你可以选择一个镜像并下载 deb 文件。

> **[下载 .deb 文件 – apt-offline](https://packages.ubuntu.com/focal/all/apt-offline/download)**

```


1.  `sudo dpkg -i name_of_package.deb`


```

### 如何更新 Ubuntu

在离线的目标系统上打开终端，使用以下命令创建一个 .sig 签名文件：

```


1.  `sudo apt-offline set  ~/offline-data.sig`


```

![](https://img.linux.net.cn/data/attachment/album/202211/14/232953ul5oqm5e4mqkqyq8.jpg)

_创建签名文件_

在这个刚创建的签名文件中，包含下载所需的软件包的路径和详细信息。

![](https://img.linux.net.cn/data/attachment/album/202211/14/232954khbk4t9lk21f1t8s.jpg)

_签名文件的内容_

把签名文件复制到 U 盘中，再插到联网的 Ubuntu 系统上。

在联网的 Ubuntu 上创建一个目录（参见下面）来存放这些文件。

打开一个终端，运行以下命令来下载所需的软件包。记得根据你的系统，更改下载目录和 .sig 签名文件的路径。

```


1.  `apt-offline get  -d ~/offline-data-dir offline-data.sig`


```

![](https://img.linux.net.cn/data/attachment/album/202211/14/232954nic476w2s2zx2z24.jpg)

_下载软件包以离线安装_

你可以看到文件相应下载，然后复制整个下载目录到 U 盘，再插到离线的 Ubuntu 系统。

运行以下命令将下载的软件包安装到离线系统，记得根据你的系统更改目录路径。

```


1.  `sudo apt-offline install offline-data-dir/`


```

![](https://img.linux.net.cn/data/attachment/album/202211/14/232954dvw3pt3m3wweks4y.jpg)

_安装软件包_

如果一切顺利，你将获得一个更新完的 Ubuntu。

重复以上步骤，就可以保持你的离线 Ubuntu 为最新版本。

希望以上教程能帮到你更新离线的 Ubuntu 系统，如果你遇到任何问题，请在下面的评论框中告诉我。

* * *

via: [https://www.debugpoint.com/how-to-update-or-upgrade-ubuntu-offline-without-internet/](https://www.debugpoint.com/how-to-update-or-upgrade-ubuntu-offline-without-internet/)

作者：[Arindam](https://www.debugpoint.com/author/admin1/) 选题：[lkxed](https://github.com/lkxed) 译者：[littlebirdnest](https://github.com/littlebirdnest) 校对：[wxy](https://github.com/wxy)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/article-15253-1.html) 荣誉推出

![](https://img.linux.net.cn/static/image/common/linisi.svg)
  

  

### 发表评论

验证码  [换一个](javascript:;)![](https://img.linux.net.cn/static/image/common/none.gif)

输入下图中的字符  
![](misc.php?mod=seccode&update=64282&idhash=cSW1dxKd)

        

**评论**

  

### 最新评论

**发表评论**

译自：[debugpoint.com](https://www.debugpoint.com/how-to-update-or-upgrade-ubuntu-offline-without-internet/) 作者： Arindam  
原创：[LCTT](https://linux.cn/lctt/) [https://linux.cn/article-15253-1.html](https://linux.cn/article-15253-1.html) 译者： littlebirdnest  
  
本文由 LCTT 原创翻译，[Linux 中国首发](https://linux.cn/article-15253-1.html)。也想加入译者行列，为开源做一些自己的贡献么？欢迎加入 [LCTT](https://linux.cn/lctt/)！  
翻译工作和译文发表仅用于学习和交流目的，翻译工作遵照 [CC-BY-SA 协议规定](https://creativecommons.org/licenses/by-sa/4.0/deed.zh)，如果我们的工作有侵犯到您的权益，请及时联系我们。  
欢迎遵照 [CC-BY-SA 协议规定](https://creativecommons.org/licenses/by-sa/4.0/deed.zh) 转载，敬请在正文中标注并保留原文/译文链接和作者/译者等信息。  
文章仅代表作者的知识和看法，如有不同观点，请楼下排队[吐槽](javascript:void(0);) :D  

_上一篇：[使用这个多功能的 Linux 命令转换音频文件](https://linux.cn/article-15246-1.html)__下一篇：[为什么有时候域名的末尾有个点？](https://linux.cn/article-15254-1.html)_

LCTT 译者

[![](https://avatars.githubusercontent.com/u/63171986?v=4)
](/lctt/littlebirdnest)

[![](https://img.linux.net.cn/static/image/common/github_icon.png)
](https://github.com/littlebirdnest) [littlebirdnest](/lctt/littlebirdnest) 🌟🌟

共计翻译： 23.0 篇 | 共计贡献： 521 天

贡献时间：2021-06-14 -> 2022-11-17

[访问我的 LCTT 主页](/lctt/littlebirdnest) | [在 GitHub 上关注我](https://github.com/littlebirdnest)

  

### 相关阅读

*   [Ubuntu](tag-Ubuntu.html)
*   [更新](tag-%E6%9B%B4%E6%96%B0.html)
*   [离线](tag-%E7%A6%BB%E7%BA%BF.html)

*   _2013-10-19_[更新了有趣细节的 Unity 8](article-2131-1-rel.html)
*   _2013-10-27_[Ubuntu 13.10 发布 - 值得升级吗 ？](article-2174-1-rel.html)
*   _2014-03-02_[Ubuntu 14.04 更新 Nautilus 和加入登陆历史](article-2613-1-rel.html)
*   _2014-03-03_[Ubuntu 每日贴士- Skype小更新，修复64位系统上PulseAudio问题](article-2619-1-rel.html)
*   _2014-05-08_[Canonical因系统安全为所有Ubuntu版本的提供内核更新](article-2988-1-rel.html)

  

 

Linux 中国 © 2003 - 2022

[京ICP备2021020457](http://www.miitbeian.gov.cn/) 京公网安备110105001595

[服务条款](https://linux.cn/legal.html) | 除特别申明外，本站原创内容版权遵循 [CC-BY-SA 协议规定](https://creativecommons.org/licenses/by-sa/4.0/deed.zh)

**返回顶部**

分享到微信

_打开微信，点击顶部的“╋”，  
使用“扫一扫”将网页分享至微信。_