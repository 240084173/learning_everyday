# CentOS 7升级gcc版本 - 姬无华 - 博客园
        CentOS 7升级gcc版本 - 姬无华 - 博客园         

*    [![](https://common.cnblogs.com/logo.svg)](https://www.cnblogs.com/ "开发者的网上家园") 
*   [首页](/)
*   [新闻](https://news.cnblogs.com/)
*   [博问](https://q.cnblogs.com/)
*   [专区](https://brands.cnblogs.com/)
*   [闪存](https://ing.cnblogs.com/)
*   [班级](https://edu.cnblogs.com/)

*    ![](https://common.cnblogs.com/images/blog/search.svg) 
    
*    [![](https://common.cnblogs.com/images/blog/newpost.svg)](https://i.cnblogs.com/EditPosts.aspx?opt=1 "写随笔") [ ![](https://common.cnblogs.com/images/blog/myblog.svg)
     ](https://passport.cnblogs.com/GetBlogApplyStatus.aspx "我的博客") [ ![](https://common.cnblogs.com/images/blog/message.svg)
      ](https://msg.cnblogs.com/ "短消息") [![](https://common.cnblogs.com/images/blog/lite-mode-on.svg)](javascript:void(0) "简洁模式启用，您在访问他人博客时会使用简洁款皮肤展示") 
    
     [![](https://common.cnblogs.com/images/blog/avatar-default.svg)](https://home.cnblogs.com/) 
    
    [我的博客](https://passport.cnblogs.com/GetBlogApplyStatus.aspx) [我的园子](https://home.cnblogs.com/) [账号设置](https://account.cnblogs.com/settings/account) [简洁模式 ![](https://www.cnblogs.com/images/lite-mode-check.svg)
    ... ](javascript:void(0) "简洁模式会使用简洁款皮肤显示所有博客") [退出登录](javascript:void(0))
    
    [注册](https://account.cnblogs.com/signup) [登录](javascript:void(0);)

[![](https://www.cnblogs.com/skins/custom/images/logo.gif)
](https://www.cnblogs.com/jixiaohua/) 

[晨雾歌谣](https://www.cnblogs.com/jixiaohua/)
==========================================

我们总要走过许多的弯路，才能到达想去的地方
---------------------

*   [博客园](https://www.cnblogs.com/)
*   [首页](https://www.cnblogs.com/jixiaohua/)
*   [新随笔](https://i.cnblogs.com/EditPosts.aspx?opt=1)
*   [联系](https://msg.cnblogs.com/send/%E5%A7%AC%E6%97%A0%E5%8D%8E)

*   [管理](https://i.cnblogs.com/)

随笔 - 146 文章 - 0 评论 - 37 阅读 - 31万

[CentOS 7升级gcc版本](https://www.cnblogs.com/jixiaohua/p/11732225.html)
====================================================================

Centos 7默认gcc版本为4.8，有时需要更高版本的，这里以升级至8.3.1版本为例，分别执行下面三条命令即可，无需手动[下载源码](http://ftp.gnu.org/gnu/gcc/)编译

1、安装centos-release-scl

sudo yum install centos-release-scl

2、安装devtoolset，注意，如果想安装7.\*版本的，就改成devtoolset-7-gcc\*，以此类推

sudo yum install devtoolset-8\-gcc\*

3、激活对应的devtoolset，所以你可以一次安装多个版本的devtoolset，需要的时候用下面这条命令切换到对应的版本

scl enable devtoolset-8 bash

大功告成，查看一下gcc版本

gcc -v

显示为 gcc version 8.3.1 20190311 (Red Hat 8.3.1-3) (GCC)

补充：这条激活命令只对本次会话有效，重启会话后还是会变回原来的4.8.5版本，要想随意切换可按如下操作。

首先，安装的devtoolset是在 /opt/rh 目录下的，如图

[![](https://img2018.cnblogs.com/blog/1604637/201910/1604637-20191024223407302-2113469117.png)
](https://img2018.cnblogs.com/blog/1604637/201910/1604637-20191024223407302-2113469117.png)

 每个版本的目录下面都有个 enable 文件，如果需要启用某个版本，只需要执行

source ./enable

所以要想切换到某个版本，只需要执行

source /opt/rh/devtoolset-8/enable

可以将对应版本的切换命令写个shell文件放在配了环境变量的目录下，需要时随时切换，或者开机自启

4、直接替换旧的gcc

旧的gcc是运行的 /usr/bin/gcc，所以将该目录下的gcc/g++替换为刚安装的新版本gcc软连接，免得每次enable

[](javascript:void(0); "复制代码")[![](https://common.cnblogs.com/images/copycode.gif)
](//common.cnblogs.com/images/copycode.gif)

mv /usr/bin/gcc /usr/bin/gcc\-4.8.5

ln -s /opt/rh/devtoolset-8/root/bin/gcc /usr/bin/gcc

mv /usr/bin/g++ /usr/bin/g++-4.8.5

ln -s /opt/rh/devtoolset-8/root/bin/g++ /usr/bin/g++

gcc --version

g++ --version

[](javascript:void(0); "复制代码")[![](https://common.cnblogs.com/images/copycode.gif)
](//common.cnblogs.com/images/copycode.gif)

  

\_\_EOF\_\_

[![](https://pic.cnblogs.com/face/1604637/20190217011124.png)
](https://pic.cnblogs.com/face/1604637/20190217011124.png)

*   **本文作者：**  [JiXiaoHua](https://www.cnblogs.com/jixiaohua)
*   **本文链接：**  [https://www.cnblogs.com/jixiaohua/p/11732225.html](https://www.cnblogs.com/jixiaohua/p/11732225.html)
*   **关于博主：**  评论和私信会在第一时间回复。或者[直接私信](https://msg.cnblogs.com/msg/send/jixiaohua)我。
*   **版权声明：**  本博客所有文章除特别声明外，均采用 [BY-NC-SA](https://creativecommons.org/licenses/by-nc-nd/4.0/ "BY-NC-SA") 许可协议。转载请注明出处！
*   **声援博主：**  如果您觉得文章对您有帮助，可以点击文章右下角**【[推荐](javascript:void(0);)】** 一下。

分类: [Linux](https://www.cnblogs.com/jixiaohua/category/1404339.html), [C/C++](https://www.cnblogs.com/jixiaohua/category/1404338.html)

[好文要顶](javascript:void(0);)推荐该文

[关注我](javascript:void(0);)关注博主关注博主 [收藏该文](javascript:void(0);)收藏本文 [![](https://common.cnblogs.com/images/icon_weibo_24.png)
](javascript:void(0); "分享至新浪微博")分享微博 [![](https://common.cnblogs.com/images/wechat.png)
](javascript:void(0); "分享至微信")分享微信

[![](https://pic.cnblogs.com/face/1604637/20190217011124.png)
](https://home.cnblogs.com/u/jixiaohua/)

[姬无华](https://home.cnblogs.com/u/jixiaohua/)  
[粉丝 - 45](https://home.cnblogs.com/u/jixiaohua/followers/) [关注 - 11](https://home.cnblogs.com/u/jixiaohua/followees/)  

[+加关注](javascript:void(0);)

10

1

[«](https://www.cnblogs.com/jixiaohua/p/11729762.html) 上一篇： [怎样判断一个exe可执行程序是32位的还是64位的（转）](https://www.cnblogs.com/jixiaohua/p/11729762.html "发布于 2019-10-23 23:18")  
[»](https://www.cnblogs.com/jixiaohua/p/11735206.html) 下一篇： [（转载）设置虚拟机桥接模式以及解决桥接模式上不了网以及ping不通主机的问题](https://www.cnblogs.com/jixiaohua/p/11735206.html "发布于 2019-10-24 21:53")

posted @ 2019-10-24 14:59  [姬无华](https://www.cnblogs.com/jixiaohua/)  阅读(54094)  评论(6)  [编辑](https://i.cnblogs.com/EditPosts.aspx?postid=11732225)  [收藏](javascript:void(0))  [举报](javascript:void(0))

[刷新评论](javascript:void(0);)[刷新页面](#)[返回顶部](#top)

登录后才能查看或发表评论，立即 [登录](javascript:void(0);) 或者 [逛逛](https://www.cnblogs.com/) 博客园首页

[【推荐】腾讯云多款云产品1折起，买云服务器送免费机器](https://curl.qcloud.com/k19RDMHo)  
[【推荐】天翼云新客特惠，云主机1核2G低至33.43元/年](https://click.ctyun.cn?track=source_bokeyuan-medium_cps-content_se430382)  

**编辑推荐：**   
· [细聊 .Net Core 中 IServiceScope 的工作方式](https://www.cnblogs.com/wucy/p/16791563.html)  
· [记一次 .NET 某企业OA后端服务 卡死分析](https://www.cnblogs.com/huangxincheng/p/16790444.html)  
· [颜色也有距离？一键找出上万个文件中的相近颜色并替换](https://www.cnblogs.com/hashtang/p/16789259.html)  
· [10分钟教你写一个数据库](https://www.cnblogs.com/ilovejaney/p/16787328.html)  
· [记一次 .NET 某电子病历 CPU 爆高分析](https://www.cnblogs.com/huangxincheng/p/16783304.html)  

**最新新闻**：  
· [波士顿动力再惊艳！机器人大秀男团舞，举手投足人味满满，多次转卖后展示新标签](//news.cnblogs.com/n/730027/)  
· [2022，社交网络危局](//news.cnblogs.com/n/730026/)  
· [蔚来李斌：特斯拉如果不改进产品和服务，很快会被市场淘汰](//news.cnblogs.com/n/730025/)  
· [头显戴上就吐， 小扎长腿竟是“诈骗”！烧完100亿美元，元宇宙大翻车](//news.cnblogs.com/n/730024/)  
· [华为大疆入场，小鹏骑虎难下？](//news.cnblogs.com/n/730023/)  
» [更多新闻...](https://news.cnblogs.com/ "IT 新闻")

CentOS 7升级gcc版本 \_
==================

19/10/24 14:5954094610  
11582:18 ~ 3:51

[Linux](https://www.cnblogs.com/jixiaohua/category/1404339.html)[C/C++](https://www.cnblogs.com/jixiaohua/category/1404338.html)

[Scroll Down](javascript:void(0);)

![](https://pic.cnblogs.com/face/1604637/20190217011124.png)

昵称： [姬无华](https://home.cnblogs.com/u/jixiaohua/)  
园龄： [3年8个月](https://home.cnblogs.com/u/jixiaohua/ "入园时间：2019-02-17")  
粉丝： [45](https://home.cnblogs.com/u/jixiaohua/followers/)  
关注： [11](https://home.cnblogs.com/u/jixiaohua/followees/)

[+加关注](javascript:void(0))

*   [首页](https://www.cnblogs.com/jixiaohua)
*   [联系](https://msg.cnblogs.com/send/jixiaohua)
*   [订阅](javascript:void(0))
*   [管理](https://i.cnblogs.com/)

| 
| [<](javascript:void(0);) | 2022年10月 | [\>](javascript:void(0);) | |
| 日 | 一 | 二 | 三 | 四 | 五 | 六 |
| 25 | 26 | 27 | 28 | 29 | 30 | 1 |
| 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| 9 | 10 | 11 | 12 | 13 | 14 | 15 |
| 16 | 17 | 18 | 19 | 20 | 21 | 22 |
| 23 | 24 | 25 | 26 | 27 | 28 | 29 |
| 30 | 31 | 1 | 2 | 3 | 4 | 5 |

找找看

积分排名

*   [积分 - 158622](javascript:void(0);)
*   [排名 - 7106](javascript:void(0);)

最新随笔

*   [gdiplus 从内存加载绘制图片](https://www.cnblogs.com/jixiaohua/p/16137183.html)
*   [ffmpeg avformat\_open\_input 返回 -1094995529 问题排查](https://www.cnblogs.com/jixiaohua/p/16134272.html)
*   [ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
*   [D3D9纹理内存释放问题](https://www.cnblogs.com/jixiaohua/p/15908565.html)
*   [Windows10 Linux开发环境搭建（WSL）](https://www.cnblogs.com/jixiaohua/p/15533539.html)
*   [C++常见面试题(转)](https://www.cnblogs.com/jixiaohua/p/15260160.html)
*   [ffmpeg解码h264 Increasing reorder buffer](https://www.cnblogs.com/jixiaohua/p/14543076.html)
*   [Chrome浏览器关联文件图标空白问题解决方案](https://www.cnblogs.com/jixiaohua/p/14343452.html)
*   [ffplay源码分析（转）](https://www.cnblogs.com/jixiaohua/p/13884828.html)
*   [(转)Qt之QNetworkProxy（网络代理）](https://www.cnblogs.com/jixiaohua/p/13831481.html)

我的标签

*   [JavaScript(31)](https://www.cnblogs.com/jixiaohua/tag/JavaScript/)
*   [ES6(22)](https://www.cnblogs.com/jixiaohua/tag/ES6/)
*   [c/c++(8)](https://www.cnblogs.com/jixiaohua/tag/c%2Fc%2B%2B/)
*   [WebAssembly(6)](https://www.cnblogs.com/jixiaohua/tag/WebAssembly/)
*   [WebRTC(5)](https://www.cnblogs.com/jixiaohua/tag/WebRTC/)
*   [Java(3)](https://www.cnblogs.com/jixiaohua/tag/Java/)
*   [Linux(3)](https://www.cnblogs.com/jixiaohua/tag/Linux/)
*   [网络协议(2)](https://www.cnblogs.com/jixiaohua/tag/%E7%BD%91%E7%BB%9C%E5%8D%8F%E8%AE%AE/)
*   [opengl(2)](https://www.cnblogs.com/jixiaohua/tag/opengl/)
*   [Make(1)](https://www.cnblogs.com/jixiaohua/tag/Make/)
*   [更多](https://www.cnblogs.com/jixiaohua/tag/)

随笔分类

*   [C/C++(59)](https://www.cnblogs.com/jixiaohua/category/1404338.html)
*   [Java (5)](https://www.cnblogs.com/jixiaohua/category/1404337.html)
*   [JavaScript(32)](https://www.cnblogs.com/jixiaohua/category/1404343.html)
*   [Linux(10)](https://www.cnblogs.com/jixiaohua/category/1404339.html)
*   [Nodejs(8)](https://www.cnblogs.com/jixiaohua/category/1404341.html)
*   [OpenGL(5)](https://www.cnblogs.com/jixiaohua/category/1609349.html)
*   [QT(6)](https://www.cnblogs.com/jixiaohua/category/1751523.html)
*   [Redis(1)](https://www.cnblogs.com/jixiaohua/category/1404340.html)
*   [WebAssembly(6)](https://www.cnblogs.com/jixiaohua/category/1404779.html)
*   [WebRTC(6)](https://www.cnblogs.com/jixiaohua/category/1570352.html)
*   [Windows (3)](https://www.cnblogs.com/jixiaohua/category/1404335.html)
*   [机器学习(1)](https://www.cnblogs.com/jixiaohua/category/1449233.html)
*   [面试题 (3)](https://www.cnblogs.com/jixiaohua/category/1404336.html)
*   [前端(6)](https://www.cnblogs.com/jixiaohua/category/1602591.html)
*   [音视频(10)](https://www.cnblogs.com/jixiaohua/category/1609343.html)

文章分类

阅读排行

*   [CentOS 7升级gcc版本(54091)](https://www.cnblogs.com/jixiaohua/p/11732225.html)
*   [windows下使用make(25746)](https://www.cnblogs.com/jixiaohua/p/11724218.html)
*   [C语言字符串操作函数总结(19341)](https://www.cnblogs.com/jixiaohua/p/11330096.html)
*   [WebAssembly学习(一)：认识WebAssembly(18859)](https://www.cnblogs.com/jixiaohua/p/10425805.html)
*   [C语言的常用printf打印占位符%d, %u, %f, %s, %c, %o, %x(14184)](https://www.cnblogs.com/jixiaohua/p/11070772.html)

推荐排行

*   [CentOS 7升级gcc版本(10)](https://www.cnblogs.com/jixiaohua/p/11732225.html)
*   [C语言字符串操作函数总结(4)](https://www.cnblogs.com/jixiaohua/p/11330096.html)
*   [ES6学习笔记（二十二）ArrayBuffer(3)](https://www.cnblogs.com/jixiaohua/p/10714662.html)
*   [WebAssembly学习(一)：认识WebAssembly(2)](https://www.cnblogs.com/jixiaohua/p/10425805.html)
*   [ffmpeg avformat\_open\_input 返回 -1094995529 问题排查(1)](https://www.cnblogs.com/jixiaohua/p/16134272.html)

最新评论

*   [Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
    
    @惟以一壶消长夏 那只有看看码流了，用ffmpeg推个文件，分别用wireshark抓一下ffmpeg推出去的流和客户端从nginx上收到的流，看看有什么异常。 ffplay不能播放看是不是rtmp地...
    
    \--姬无华
    
*   [Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
    
    @姬无华 1.客户端我们这边一直没变过，使用的flv.js是18年的版本了，是没有适配FFmpeg更新的问题？ 2.我这边使用ffplay在客户端无法访问到服务器端的rtmp流，不清楚是啥原因 3.我...
    
    \--惟以一壶消长夏
    
*   [Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
    
    @惟以一壶消长夏 不一定，按你说的out\_queue 和out\_cork调大可以缓解这种情况来看，rtmp使用tcp传输，如果客户端flv.js无法消耗掉接收端的数据，导致nginx发送端tcp数据发...
    
    \--姬无华
    
*   [Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
    
    @姬无华 看情况这种无法播放的视频是偶现的，如果我把nginx的配置文件中的参数out\_queue 和out\_cork调的非常大，这种偶现情况会有所缓解，能够播放九路视频，但是多次切换播放后，还是会偶...
    
    \--惟以一壶消长夏
    
*   [Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
    
    @惟以一壶消长夏 这个我也没用过，看前台报错像是flv.js识别不了流格式，而nginx报超时可能是ffmpeg的流没推上来或者格式不对，只能提供一点排查思路： 先用VLC或ffplay直接播放一下f...
    
    \--姬无华
    

文章档案

随笔档案

*   [2022年4月(2)](https://www.cnblogs.com/jixiaohua/archive/2022/04.html)
*   [2022年3月(1)](https://www.cnblogs.com/jixiaohua/archive/2022/03.html)
*   [2022年2月(1)](https://www.cnblogs.com/jixiaohua/archive/2022/02.html)
*   [2021年11月(1)](https://www.cnblogs.com/jixiaohua/archive/2021/11.html)
*   [2021年9月(1)](https://www.cnblogs.com/jixiaohua/archive/2021/09.html)
*   [2021年3月(1)](https://www.cnblogs.com/jixiaohua/archive/2021/03.html)
*   [2021年1月(1)](https://www.cnblogs.com/jixiaohua/archive/2021/01.html)
*   [2020年10月(4)](https://www.cnblogs.com/jixiaohua/archive/2020/10.html)
*   [2020年7月(2)](https://www.cnblogs.com/jixiaohua/archive/2020/07.html)
*   [2020年5月(3)](https://www.cnblogs.com/jixiaohua/archive/2020/05.html)
*   [2020年4月(2)](https://www.cnblogs.com/jixiaohua/archive/2020/04.html)
*   [2020年3月(3)](https://www.cnblogs.com/jixiaohua/archive/2020/03.html)
*   [2020年2月(2)](https://www.cnblogs.com/jixiaohua/archive/2020/02.html)
*   [2020年1月(12)](https://www.cnblogs.com/jixiaohua/archive/2020/01.html)
*   [2019年12月(24)](https://www.cnblogs.com/jixiaohua/archive/2019/12.html)
*   [2019年11月(7)](https://www.cnblogs.com/jixiaohua/archive/2019/11.html)
*   [2019年10月(12)](https://www.cnblogs.com/jixiaohua/archive/2019/10.html)
*   [2019年9月(3)](https://www.cnblogs.com/jixiaohua/archive/2019/09.html)
*   [2019年8月(9)](https://www.cnblogs.com/jixiaohua/archive/2019/08.html)
*   [2019年7月(2)](https://www.cnblogs.com/jixiaohua/archive/2019/07.html)
*   [2019年6月(5)](https://www.cnblogs.com/jixiaohua/archive/2019/06.html)
*   [2019年5月(1)](https://www.cnblogs.com/jixiaohua/archive/2019/05.html)
*   [2019年4月(10)](https://www.cnblogs.com/jixiaohua/archive/2019/04.html)
*   [2019年3月(22)](https://www.cnblogs.com/jixiaohua/archive/2019/03.html)
*   [2019年2月(10)](https://www.cnblogs.com/jixiaohua/archive/2019/02.html)
*   [2018年12月(5)](https://www.cnblogs.com/jixiaohua/archive/2018/12.html)
*   [更多](javascript:void(0))

Close Menu

Created with Snap

MENU

### 公告

文章目录

访问主页

10

1

 Alipay

 WeChat

qrCode

关注

点击开启

跳至底部

昵称： [姬无华](https://home.cnblogs.com/u/jixiaohua/)  
园龄： [3年8个月](https://home.cnblogs.com/u/jixiaohua/ "入园时间：2019-02-17")  
粉丝： [45](https://home.cnblogs.com/u/jixiaohua/followers/)  
关注： [11](https://home.cnblogs.com/u/jixiaohua/followees/)

[+加关注](javascript:void(0))

### 搜索

 

### 常用链接

*   [我的随笔](https://www.cnblogs.com/jixiaohua/p/ "我的博客的随笔列表")
*   [我的评论](https://www.cnblogs.com/jixiaohua/MyComments.html "我的发表过的评论列表")
*   [我的参与](https://www.cnblogs.com/jixiaohua/OtherPosts.html "我评论过的随笔列表")
*   [最新评论](https://www.cnblogs.com/jixiaohua/comments "我的博客的评论列表")
*   [我的标签](https://www.cnblogs.com/jixiaohua/tag/ "我的博客的标签列表")

### 最新随笔

*   [1.gdiplus 从内存加载绘制图片](https://www.cnblogs.com/jixiaohua/p/16137183.html)
*   [2.ffmpeg avformat\_open\_input 返回 -1094995529 问题排查](https://www.cnblogs.com/jixiaohua/p/16134272.html)
*   [3.ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
*   [4.D3D9纹理内存释放问题](https://www.cnblogs.com/jixiaohua/p/15908565.html)
*   [5.Windows10 Linux开发环境搭建（WSL）](https://www.cnblogs.com/jixiaohua/p/15533539.html)
*   [6.C++常见面试题(转)](https://www.cnblogs.com/jixiaohua/p/15260160.html)
*   [7.ffmpeg解码h264 Increasing reorder buffer](https://www.cnblogs.com/jixiaohua/p/14543076.html)
*   [8.Chrome浏览器关联文件图标空白问题解决方案](https://www.cnblogs.com/jixiaohua/p/14343452.html)
*   [9.ffplay源码分析（转）](https://www.cnblogs.com/jixiaohua/p/13884828.html)
*   [10.(转)Qt之QNetworkProxy（网络代理）](https://www.cnblogs.com/jixiaohua/p/13831481.html)

### 我的标签

*   [JavaScript(31)](https://www.cnblogs.com/jixiaohua/tag/JavaScript/)
*   [ES6(22)](https://www.cnblogs.com/jixiaohua/tag/ES6/)
*   [c/c++(8)](https://www.cnblogs.com/jixiaohua/tag/c%2Fc%2B%2B/)
*   [WebAssembly(6)](https://www.cnblogs.com/jixiaohua/tag/WebAssembly/)
*   [WebRTC(5)](https://www.cnblogs.com/jixiaohua/tag/WebRTC/)
*   [Java(3)](https://www.cnblogs.com/jixiaohua/tag/Java/)
*   [Linux(3)](https://www.cnblogs.com/jixiaohua/tag/Linux/)
*   [网络协议(2)](https://www.cnblogs.com/jixiaohua/tag/%E7%BD%91%E7%BB%9C%E5%8D%8F%E8%AE%AE/)
*   [opengl(2)](https://www.cnblogs.com/jixiaohua/tag/opengl/)
*   [Make(1)](https://www.cnblogs.com/jixiaohua/tag/Make/)
*   [更多](https://www.cnblogs.com/jixiaohua/tag/)

### 积分与排名

*   积分 - 158622
*   排名 - 7106

### [随笔分类](https://www.cnblogs.com/jixiaohua/categories)

*   [C/C++(59)](https://www.cnblogs.com/jixiaohua/category/1404338.html)
*   [Java (5)](https://www.cnblogs.com/jixiaohua/category/1404337.html)
*   [JavaScript(32)](https://www.cnblogs.com/jixiaohua/category/1404343.html)
*   [Linux(10)](https://www.cnblogs.com/jixiaohua/category/1404339.html)
*   [Nodejs(8)](https://www.cnblogs.com/jixiaohua/category/1404341.html)
*   [OpenGL(5)](https://www.cnblogs.com/jixiaohua/category/1609349.html)
*   [QT(6)](https://www.cnblogs.com/jixiaohua/category/1751523.html)
*   [Redis(1)](https://www.cnblogs.com/jixiaohua/category/1404340.html)
*   [WebAssembly(6)](https://www.cnblogs.com/jixiaohua/category/1404779.html)
*   [WebRTC(6)](https://www.cnblogs.com/jixiaohua/category/1570352.html)
*   [Windows (3)](https://www.cnblogs.com/jixiaohua/category/1404335.html)
*   [机器学习(1)](https://www.cnblogs.com/jixiaohua/category/1449233.html)
*   [面试题 (3)](https://www.cnblogs.com/jixiaohua/category/1404336.html)
*   [前端(6)](https://www.cnblogs.com/jixiaohua/category/1602591.html)
*   [音视频(10)](https://www.cnblogs.com/jixiaohua/category/1609343.html)

### 随笔档案

*   [2022年4月(2)](https://www.cnblogs.com/jixiaohua/archive/2022/04.html)
*   [2022年3月(1)](https://www.cnblogs.com/jixiaohua/archive/2022/03.html)
*   [2022年2月(1)](https://www.cnblogs.com/jixiaohua/archive/2022/02.html)
*   [2021年11月(1)](https://www.cnblogs.com/jixiaohua/archive/2021/11.html)
*   [2021年9月(1)](https://www.cnblogs.com/jixiaohua/archive/2021/09.html)
*   [2021年3月(1)](https://www.cnblogs.com/jixiaohua/archive/2021/03.html)
*   [2021年1月(1)](https://www.cnblogs.com/jixiaohua/archive/2021/01.html)
*   [2020年10月(4)](https://www.cnblogs.com/jixiaohua/archive/2020/10.html)
*   [2020年7月(2)](https://www.cnblogs.com/jixiaohua/archive/2020/07.html)
*   [2020年5月(3)](https://www.cnblogs.com/jixiaohua/archive/2020/05.html)
*   [2020年4月(2)](https://www.cnblogs.com/jixiaohua/archive/2020/04.html)
*   [2020年3月(3)](https://www.cnblogs.com/jixiaohua/archive/2020/03.html)
*   [2020年2月(2)](https://www.cnblogs.com/jixiaohua/archive/2020/02.html)
*   [2020年1月(12)](https://www.cnblogs.com/jixiaohua/archive/2020/01.html)
*   [2019年12月(24)](https://www.cnblogs.com/jixiaohua/archive/2019/12.html)
*   [2019年11月(7)](https://www.cnblogs.com/jixiaohua/archive/2019/11.html)
*   [2019年10月(12)](https://www.cnblogs.com/jixiaohua/archive/2019/10.html)
*   [2019年9月(3)](https://www.cnblogs.com/jixiaohua/archive/2019/09.html)
*   [2019年8月(9)](https://www.cnblogs.com/jixiaohua/archive/2019/08.html)
*   [2019年7月(2)](https://www.cnblogs.com/jixiaohua/archive/2019/07.html)
*   [2019年6月(5)](https://www.cnblogs.com/jixiaohua/archive/2019/06.html)
*   [2019年5月(1)](https://www.cnblogs.com/jixiaohua/archive/2019/05.html)
*   [2019年4月(10)](https://www.cnblogs.com/jixiaohua/archive/2019/04.html)
*   [2019年3月(22)](https://www.cnblogs.com/jixiaohua/archive/2019/03.html)
*   [2019年2月(10)](https://www.cnblogs.com/jixiaohua/archive/2019/02.html)
*   [2018年12月(5)](https://www.cnblogs.com/jixiaohua/archive/2018/12.html)
*   [更多](javascript:void(0))

### [阅读排行榜](https://www.cnblogs.com/jixiaohua/most-viewed)

*   [1\. CentOS 7升级gcc版本(54091)](https://www.cnblogs.com/jixiaohua/p/11732225.html)
*   [2\. windows下使用make(25746)](https://www.cnblogs.com/jixiaohua/p/11724218.html)
*   [3\. C语言字符串操作函数总结(19341)](https://www.cnblogs.com/jixiaohua/p/11330096.html)
*   [4\. WebAssembly学习(一)：认识WebAssembly(18859)](https://www.cnblogs.com/jixiaohua/p/10425805.html)
*   [5\. C语言的常用printf打印占位符%d, %u, %f, %s, %c, %o, %x(14184)](https://www.cnblogs.com/jixiaohua/p/11070772.html)

### [评论排行榜](https://www.cnblogs.com/jixiaohua/most-commented)

*   [1\. ffmpeg hls拉流超时问题(6)](https://www.cnblogs.com/jixiaohua/p/16035174.html)
*   [2\. CentOS 7升级gcc版本(6)](https://www.cnblogs.com/jixiaohua/p/11732225.html)
*   [3\. ES6学习笔记（十二）异步解决方案Promise(4)](https://www.cnblogs.com/jixiaohua/p/10569284.html)
*   [4\. mediasoup-demo解析-服务端(3)](https://www.cnblogs.com/jixiaohua/p/11593549.html)
*   [5\. ES6学习笔记（二十二）ArrayBuffer(3)](https://www.cnblogs.com/jixiaohua/p/10714662.html)

### [推荐排行榜](https://www.cnblogs.com/jixiaohua/most-liked)

*   [1\. CentOS 7升级gcc版本(10)](https://www.cnblogs.com/jixiaohua/p/11732225.html)
*   [2\. C语言字符串操作函数总结(4)](https://www.cnblogs.com/jixiaohua/p/11330096.html)
*   [3\. ES6学习笔记（二十二）ArrayBuffer(3)](https://www.cnblogs.com/jixiaohua/p/10714662.html)
*   [4\. WebAssembly学习(一)：认识WebAssembly(2)](https://www.cnblogs.com/jixiaohua/p/10425805.html)
*   [5\. ffmpeg avformat\_open\_input 返回 -1094995529 问题排查(1)](https://www.cnblogs.com/jixiaohua/p/16134272.html)

### [最新评论](https://www.cnblogs.com/jixiaohua/comments)

*   [1\. Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
*   @惟以一壶消长夏 那只有看看码流了，用ffmpeg推个文件，分别用wireshark抓一下ffmpeg推出去的流和客户端从nginx上收到的流，看看有什么异常。 ffplay不能播放看是不是rtmp地...
*   \--姬无华
*   [2\. Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
*   @姬无华 1.客户端我们这边一直没变过，使用的flv.js是18年的版本了，是没有适配FFmpeg更新的问题？ 2.我这边使用ffplay在客户端无法访问到服务器端的rtmp流，不清楚是啥原因 3.我...
*   \--惟以一壶消长夏
*   [3\. Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
*   @惟以一壶消长夏 不一定，按你说的out\_queue 和out\_cork调大可以缓解这种情况来看，rtmp使用tcp传输，如果客户端flv.js无法消耗掉接收端的数据，导致nginx发送端tcp数据发...
*   \--姬无华
*   [4\. Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
*   @姬无华 看情况这种无法播放的视频是偶现的，如果我把nginx的配置文件中的参数out\_queue 和out\_cork调的非常大，这种偶现情况会有所缓解，能够播放九路视频，但是多次切换播放后，还是会偶...
*   \--惟以一壶消长夏
*   [5\. Re:ffmpeg hls拉流超时问题](https://www.cnblogs.com/jixiaohua/p/16035174.html)
*   @惟以一壶消长夏 这个我也没用过，看前台报错像是flv.js识别不了流格式，而nginx报超时可能是ffmpeg的流没推上来或者格式不对，只能提供一点排查思路： 先用VLC或ffplay直接播放一下f...
*   \--姬无华

\[ ##textLeft## ##textRight## \]

This blog has running : 1349 d 16 h 27 m 26 s ღゝ◡╹)ノ♡

##linksHtml##

##cnzzHtml##

Copyright © 2022 姬无华 Powered by .NET 6 on Kubernetes