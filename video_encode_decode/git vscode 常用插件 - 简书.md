# git vscode 常用插件 - 简书
git vscode 常用插件 - 简书

[](/)

[登录](/sign_in)[注册](/sign_up)[写文章](/writer)

[首页](/)[下载APP](/apps?utm_medium=desktop&utm_source=navbar-apps)[会员](/vips)[IT技术](/techareas)

git vscode 常用插件
===============

[![](https://upload.jianshu.io/users/upload_avatars/26381799/75a60020-424c-4176-a0f0-b2184336ffad?imageMogr2/auto-orient/strip|imageView2/1/w/80/h/80/format/webp)
暴躁程序员](/u/29ce491fa28a)关注赞赏支持

git vscode 常用插件
===============

[![](https://upload.jianshu.io/users/upload_avatars/26381799/75a60020-424c-4176-a0f0-b2184336ffad?imageMogr2/auto-orient/strip|imageView2/1/w/96/h/96/format/webp)
](/u/29ce491fa28a)

[暴躁程序员](/u/29ce491fa28a)关注

2022.05.13 14:35:30字数 932阅读 2,267

1\. git 必备插件：GitLens —— Git superchanged
========================================

在源代码管理模式下，左侧下方的几个列表就是 GitLens —— Git superchanged 插件的展示操作区

###### 1\. COMMITS 提交记录：

展示整个提交记录、提交前后文件对比、打开提交文件、推送、拉取、切换分支等

1.  打开提交文件：在 COMMITS 里面，单击openfile图标打开提交的文件 或者 在路径上右键Open File
2.  推送、拉取、切换分支：在 COMMITS 展开后，点击最上方图标可进行推送、拉取、切换分支等
3.  提交记录对照：在 COMMITS 里面选中提交记录，右键 Open Changes  
    Open Changes with Working File --- 选中提交记录和最新提交记录做对照  
    Open Previous Changes with Working File --- 选中提交记录的上一条提交记录和最新提交记录做对照  
    Open Changes with Revison --- 选中提交记录和其他再次选中的提交记录做对照

###### 2\. FILE HISTORY 文件历史记录:

展示目标文件的历史记录、打开历史记录文件、当前历史记录文件和不同时期的历史记录对照

1.  选中目标文件：展开左侧文件列表树，选中目标文件，右键点击 Open File History，FILE HISTORY会自动切换成当前文件的历史记录
2.  打开历史文件：在 FILE HISTORY 里面选中历史记录，右键 Open File
3.  历史记录对照：在 FILE HISTORY 里面选中历史记录，右键 Open Changes  
    Open Changes with Working File --- 选中历史记录和最新历史记录做对照  
    Open Previous Changes with Working File --- 选中历史记录的上一条历史记录和最新历史记录做对照  
    Open Changes with Revison --- 选中历史记录和其他再次选中的历史记录做对照

###### 3\. BRANCHES 现有分支:

展示拉取过的分支、查看哪些分支线上代码更新、切换分支、拉取（pull）

1.  查看哪些分支线上代码更新：在 BRANCHES 里，有代码更新的分支呈现橙红色
2.  切换分支、拉取：在 BRANCHES 里右侧图标

###### 4\. REMOTES 远程所有分支:

展示所有远程分支，可查看远程分支上的提交内容

2\. git 历史插件：Git history
========================

和 GitLens —— Git superchanged 相比，更有针对性  
调起当前分支的Git history：在源代码管理模式下点击上方的逆时针表的图标  
调起当前分支下当前分级的Git history：直接右键 GIT:View File History

1.  可视化直观展示历史记录
2.  可获取提交id
3.  软\\硬回滚
4.  在历史记录基础上新建分支、
5.  将当前历史记录内容和并到当前分支上
6.  可选择分支（默认显示当前分支的历史记录）
7.  可通过作者、标题来过滤历史记录
8.  将当前分支切换到当前历史记录分支（点击绿色），删除远程分支（点击红色）
9.  获取文件当前行修改的历史记录：打开文件代码，将光标锁定在当前行，右键，GIT:View Line History

3\. git 可视化插件：Git Graph
=======================

调起Git Graph：在源代码管理模式下点击上方的树杈状的图标 或者 点击左下角的 Git Graph

1.  可直观的看到提交记录的注释、时间、作者、commitid等
2.  可选择不同分支，也可多选几个分支
3.  获取commit id ：右键 Copy Commit Hash
4.  显示当前文件的提交差异对照

0人点赞

[git](/nb/51910876)

更多精彩内容，就在简书APP

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABacAAAWnCAMAAABgpz87AAAAh1BMVEX////aZWf45eL99/bcb2788O3ijojeeXf0083vwLnprKbghIDstq/no5zxysT33NjkmJL++vraZ2jklI7ffnv88/HbbGzbaWnoqKH+/f366ebmnJX119LddnPccnH44NzrsaruvLbii4b77evzzsjwx8D22tXhh4PnoJntubLww7z449/deHYjPTZEAAAwHklEQVR42uzBgQAAAACAoP2pF6kCAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAGD24EAAAAAAAMj/tRFUVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVYU9OBAAAAAAAPJ/bQRVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVWEPDgQAAAAAgPxfG0FVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVdiDAwEAAAAAIP/XRlBVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVFfbgQAAAAAAAyP+1EVRVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVhT04EAAAAAAA8n9tBFVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVYQ8OBAAAAACA/F8bQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV2IMDAQAAAAAg/9dGUFVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVUV9uCQAAAAAEDQ/9dusAMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA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)

"小礼物走一走，来简书关注我"

赞赏支持还没有人赞赏，支持一下

[![](https://upload.jianshu.io/users/upload_avatars/26381799/75a60020-424c-4176-a0f0-b2184336ffad?imageMogr2/auto-orient/strip|imageView2/1/w/100/h/100/format/webp)
](/u/29ce491fa28a)

[暴躁程序员](/u/29ce491fa28a "暴躁程序员")三人行必有我师

总资产35共写了4.5W字获得332个赞共95个粉丝

关注

[

### 网易《梦幻西游网页版》，不肝不氪也能暴爽西游！

![](https://s3m.mediav.com/yiti/0304fe60be432d000033e47ba28386cb.gif)

网易游戏 · 效卓 广告

](javascript:;)

### 

全部评论0只看作者

按时间倒序

按时间正序

### 推荐阅读[更多精彩内容](/)

*   [VSCode 代码管理插件GitLens使用指南](/p/f83f319e9fb0)
    
    相信vsCode的强大功能深受开发人员的喜爱，作为前端开发的我，最近一直头疼于代码的管理与提交，这篇文章记录下vs...
    
    [![](https://upload.jianshu.io/users/upload_avatars/3236890/76b22d47-ca02-4de7-9821-e8637c0b7954.png?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    硅谷干货](/u/38a93366c8ef)阅读 7,915评论 0赞 2
    
*   [vsCode 源代码管理插件GitLens使用指南 你值得收藏](/p/95a1a06ac0fb)
    
    相信vsCode的强大功能深受开发人员的喜爱，作为前端开发的我，最近一直头疼于代码的管理与提交，这篇文章记录下vs...
    
    [![](https://cdn2.jianshu.io/assets/default_avatar/14-0651acff782e7a18653d7530d6b27661.jpg)
    大脸猫的前端之路](/u/40dc08ca40fc)阅读 39,403评论 0赞 15
    
    [![](https://upload-images.jianshu.io/upload_images/1062180-6e08b206bb7b8ad5.png?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/95a1a06ac0fb)

[

### 亚洲第一美女：跟我克拉拉混，每日20发998绝密补贴！

![](https://s3m1.fenxi.com/galileo/2dc1683124a86a93bddbab64b9db3ccb.gif)

克拉拉代言 · 效卓 广告

](javascript:;)

*   [vscode 前端常用的插件](/p/f4085defd953)
    
    插件列表： 1.Color Info 这个便捷的插件，将为你提供你在CSS 中使用颜色的相关信息。你只需在颜色...
    
    [![](https://upload.jianshu.io/users/upload_avatars/19445805/b81ec95a-a737-4502-8096-d35ce700f371.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    骑着蜗牛撵大象](/u/61f71c57bf47)阅读 4,965评论 0赞 2
    
    [![](https://upload-images.jianshu.io/upload_images/19445805-d185a53b92dee083.png?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/f4085defd953)
*   [vscode 常用插件（全面）](/p/5cbf24a00ebb)
    
    一、代码片段类插件 英文叫做Snippets\[https://link.zhihu.com/?target=htt...
    
    [![](https://cdn2.jianshu.io/assets/default_avatar/4-3397163ecdb3855a0a4139c34a695885.jpg)
    xLi\_9de0](/u/0e3842e1f69f)阅读 2,250评论 0赞 1
    
*   [第五章 vscode进行git管理](/p/304ee91310d1)
    
    目录 第一章 初次接触vscode第二章 vscode快捷键的使用第三章 vscode的界面配置第四章 vscod...
    
    [![](https://upload.jianshu.io/users/upload_avatars/14616778/7125eba0-a2b1-4a0c-85cf-8e98f4e90f86?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    小宫同学\_](/u/44f676e24c73)阅读 1,791评论 0赞 4
    
    [![](https://upload-images.jianshu.io/upload_images/14616778-b65eeff5519cf240.png?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/304ee91310d1)
*   [《How To Use Git Source Control with Xcode 9》翻译：...](/p/5ce121d462a2)
    
    刚更新完Xcode9，发现自带的Git功能的用户体验比之前版本都有很大的提升。网上搜索了一篇使用文档做一下翻译，原...
    
    [![](https://cdn2.jianshu.io/assets/default_avatar/12-aeeea4bedf10f2a12c0d50d626951489.jpg)
    ANTI\_JAM](/u/c08172500420)阅读 611评论 0赞 4
    
    [![](https://upload-images.jianshu.io/upload_images/1288594-9ce1396eee376714.png?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/5ce121d462a2)

*   [盘一盘那些提效/创意的 vscode 插件](/p/06d5e76b095d)
    
    在前端开发中，vscode 是最常用的编辑器，而 vscode 有着各种实用插件，有些可以帮助我们提升效率，有些可...
    
    [![](https://upload.jianshu.io/users/upload_avatars/6218078/9850d032-d550-4ad1-9465-2c483dd6929a.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    昵称不用太拉风](/u/318281a067b7)阅读 305评论 0赞 1
    
*   [VSCode常用插件](/p/5f64dc76f875)
    
    从IOS转前端，VSCode相对Xcode确实有很多便利之处，特别是强大的插件，用了三个小时，看了自己项目的插件，...
    
    [![](https://upload.jianshu.io/users/upload_avatars/2267599/3f8b249b386d?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    夏末秋刀鱼](/u/19867c200f12)阅读 188评论 0赞 0
    
*   [盘一盘那些提效/创意的 vscode 插件](/p/058eae8e08c0)
    
    在前端开发中，vscode 是最常用的编辑器，而 vscode 有着各种实用插件，有些可以帮助我们提升效率，有些可...
    
    [![](https://cdn2.jianshu.io/assets/default_avatar/10-e691107df16746d4a9f3fe9496fd1848.jpg)
    明源云链前端团队](/u/a6981cd25d3c)阅读 224评论 0赞 1
    
*   [怎样在Xcode 8上使用Git实现源码控制](/p/dc8ac7eba266)
    
    这是一篇翻译作品,怎样在Xcode 8上使用Git实现源码控制 文章原文地址:How To Use Git Sou...
    
    [![](https://cdn2.jianshu.io/assets/default_avatar/2-9636b13945b9ccf345bc98d0d81074eb.jpg)
    Eddy\_0](/u/bdd9f59e9a13)阅读 1,237评论 0赞 3
    
    [![](https://upload-images.jianshu.io/upload_images/808391-8cf178ad99be4f68.png?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/dc8ac7eba266)

*   [vscode常用插件](/p/ac8b35083605)
    
    一、 vscode常用插件 1. any-rule 常用正则大全 使用：按F1(或ctrl + shift + p...
    
    [![](https://upload.jianshu.io/users/upload_avatars/26128988/0c3be840-c6e1-4f74-8604-d5a6dd4001bd.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    YiYaYiYaHei](/u/58a586b54b3e)阅读 2,873评论 0赞 45
    
    [![](https://upload-images.jianshu.io/upload_images/26128988-98901837072010b3.png?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/ac8b35083605)
*   [Mac下从安装Git到使用github进行版本控制(git命令/Xcode管理)](/p/a5063d6a2c1e)
    
    引 个人在iOS的开发过程中，经常会用到第三方类库，而这些类库大都是在GitHub上的，不得不说GitHub确实是...
    
    [![](https://upload.jianshu.io/users/upload_avatars/9075967/e25a5923-c56c-4d79-bd43-28a84aca112d.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    Cloudox\_](/u/9ec19ab8c802)阅读 1,309评论 0赞 2
    
    [![](https://upload-images.jianshu.io/upload_images/9075967-1ad799890c8a7a0f.png?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/a5063d6a2c1e)
*   [Git全栈开发使用指南](/p/74fc46edfe8a)
    
    一、Git基础 1、Git简介 Git是一种分布式版本控制系统，由Linux之父Linus开发。 所谓分布式版本管...
    
    [![](https://upload.jianshu.io/users/upload_avatars/25858374/9ab2ec18-aadb-4614-b593-72138cb273f2.png?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    三分恶](/u/0ad7f32a915a)阅读 85评论 0赞 0
    
    [![](https://upload-images.jianshu.io/upload_images/25858374-0879d638ca3d8a9f.png?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/74fc46edfe8a)
*   [VScode插件推荐（全面）](/p/3eebde5748a6)
    
    工欲善其事必先利其器，以下是本人为前端开发收集的vscode插件，有需要的话赶紧mark起来吧~ 一、代码片段类插...
    
    [![](https://upload.jianshu.io/users/upload_avatars/9813501/0e6e9ecc-cf56-46e2-a481-331ed11cbfc6.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    白雪公主960](/u/199fb97d4561)阅读 182,213评论 8赞 81
    

*   [Git新手教程-标签、分支和合并(六)](/p/8ffff4b5ba9c)
    
    前言 在之前的文章中，我们已经对仓库和提交已经有一定的了解了，在该篇文章中，我们将学习git tag、git br...
    
    [![](https://upload.jianshu.io/users/upload_avatars/2824145/cabfec11-77ee-45a0-bd75-fa7ecba8be7f.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    AndyJennifer](/u/921c778fb5e1)阅读 639评论 0赞 2
    
    [![](https://upload-images.jianshu.io/upload_images/2824145-901499b32360b1e6.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/300/h/240/format/webp)
    ](/p/8ffff4b5ba9c)
*   [python-day3](/p/dcedab873fc9)
    
    字符串 1.什么是字符串 使用单引号或者双引号括起来的字符集就是字符串。 引号中单独的符号、数字、字母等叫字符。 ...
    
    [![](https://cdn2.jianshu.io/assets/default_avatar/3-9a2bcc21a5d89e21dafc73b39dc5f582.jpg)
    mango\_2e17](/u/cd7070e74d3d)阅读 6,140评论 1赞 7
    
*   [《闭上眼睛才能看清楚自己》读书分享](/p/c733ce3165fd)
    
    《闭上眼睛才能看清楚自己》这本书是香海禅寺主持贤宗法师的人生体悟，修行心得及讲学录，此书从六个章节讲述了禅修是什么...
    
    [![](https://upload.jianshu.io/users/upload_avatars/12400153/7ae71049-9f82-4d1f-afe8-2f1aca8f0e31.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    宜均](/u/7412fb0d06c8)阅读 6,282评论 0赞 23
    
*   [targetSdkVersion升级到28一些修改的地方(持续更新)](/p/6ce99e03080f)
    
    前言 Google Play应用市场对于应用的targetSdkVersion有了更为严格的要求。从 2018 年...
    
    [![](https://upload.jianshu.io/users/upload_avatars/2057980/676832e2-32a4-443b-b060-3f65eb9f557e.png?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    申国骏](/u/b692bbf77991)阅读 57,285评论 14赞 96
    

*   [见识第八章](/p/af5eb211edeb)
    
    第七章:理性的投资观 字数： 1.投资要围绕目的进行 投资的目的是为了挣钱。投资的除了金钱还有时间和精力也是一种投...
    
    [![](https://upload.jianshu.io/users/upload_avatars/5296601/52c97504-0cb4-4e02-a3f5-6891e2565cb6?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    幸福萍宝](/u/36821e249799)阅读 2,247评论 1赞 2
    
*   [PID控制（上）](/p/2f8e23c1d7b7)
    
    本文转载自微信公众号“电子搬砖师”，原文链接 这篇文章会以特别形象通俗的方式讲讲什么是PID。 很多人看到网上写的...
    
    [![](https://upload.jianshu.io/users/upload_avatars/13209038/e1217cdf-4b79-4593-b8c6-7b8ed7862ab9.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/48/h/48/format/webp)
    这个飞宏不太冷](/u/038c217ac731)阅读 4,264评论 1赞 14
    

[![](https://upload.jianshu.io/users/upload_avatars/26381799/75a60020-424c-4176-a0f0-b2184336ffad?imageMogr2/auto-orient/strip|imageView2/1/w/90/h/90/format/webp)
](/u/29ce491fa28a)

[暴躁程序员](/u/29ce491fa28a)

关注

总资产35

[JavaScript 控制异步走向的几种方式](/p/831e1fd17c1a)

阅读 74

[JavaScript 代码注释规范](/p/a8f262f609f8)

阅读 27

[vscode 注释生成插件 KoroFileHeader](/p/1f4213f97c2d)

阅读 123

### 热门故事

[超A女霸总在线撩夫](https://www.jianshu.com/p/7658350828f5)

[我把老板当金库，老板把我当老婆](https://www.jianshu.com/p/0602f56492e1)

[男神学长求放过，你的节操掉了](https://www.jianshu.com/p/df453b1aa670)

[情深见于微](https://www.jianshu.com/p/9fd77d55a21f)

### 推荐阅读

[git使用方法](/p/4f0a6b49f1ee)

阅读 99

[Github Desktop汉化程序v0.01](/p/55bce718633e)

阅读 494

[【代码管理，从小抓起】（一）](/p/2d4514d85336)

阅读 180

[git提交规范](/p/2d3679cb59ec)

阅读 794

[Git的使用](/p/a1d022110226)

阅读 164

评论0

赞

赞1赞

赞赏

更多好文

![](https://g.alicdn.com/sd-base/static/1.0.10/image/nocapture/robot.png)

为保证您的正常访问，请进行如下验证：