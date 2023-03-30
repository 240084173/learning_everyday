# 【Linux实用工具】dstat命令详解及使用场景 - 掘金
【Linux实用工具】dstat命令详解及使用场景 - 掘金 

 [![](https://lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/e08da34488b114bd4c665ba2fa520a31.svg)
 ![](https://lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/6c61ae65d1c41ae8221a670fa32d05aa.svg)](/)  

*   首页
    
    *   [首页](/)
    *   [沸点](/pins)
    *   [课程 上新](/course)
    *   [直播](/live)
    *   [活动](/events/all)
    *   [竞赛 码上报名](/challenge)
    
    [商城](https://detail.youzan.com/show/goods/newest?kdt_id=104340304)
    
    [APP](/app?utm_source=jj_nav) 邀请有礼
    
    [插件](https://juejin.cn/extension?utm_source=jj_nav)
    
    *   [![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7482b3ad2cd14edda31f05399c2ae759~tplv-k3u1fbpfcp-no-mark:230:230:230:0.awebp)
        ](https://juejin.cn/vip?utm_source=web_nav)

*   *   搜索历史 清空
        
    *   创作者中心
        
        *   写文章
            
        *   发沸点
            
        *   写笔记
            
        *   写代码
            
        *   草稿箱
            
        
        创作灵感 查看更多
        
*   ![](https://lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/24127194d5b158d7eaf8f09a256c5d01.svg)
    
    会员
    
*   登录
    
    注册
    
    登录掘金后可立即获得以下权益：
    
    *   免费试学课程
    *   收藏有用文章
    *   查阅浏览足迹
    *   订阅优质专栏
    *   体验签到抽奖
    *   提升成长等级
    
    立即登录
    
    首次使用？
    
    点我注册
    

   

 

  

【Linux实用工具】dstat命令详解及使用场景
=========================

[![](https://p3-passport.byteimg.com/img/user-avatar/6838c75c150c97db09eb7b9d186a3f45~100x100.awebp)
](/user/1626932939607166)

[左羊 ![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ad1d5b8ec0974b0bbc14446acdd7c20d~tplv-k3u1fbpfcp-no-mark:0:0:0:0.awebp)](/user/1626932939607166) 

2023年03月27日 19:38 ·  阅读 6

关注

![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a1f81826842c48e4b9a6804dc25fc0a7~tplv-k3u1fbpfcp-zoom-crop-mark:1512:1512:1512:851.awebp?)
  

文字首发于公众号|左羊公社
-------------

### Linux dstat命令详解

今天，左羊将介绍一个超级实用的Linux命令：dstat。

dstat是一个Linux系统监控工具，可以提供实时的系统性能数据，包括CPU、内存、磁盘I/O、网络流量等等。在发现系统性能问题时，dstat可以帮助我们快速准确的找到问题所在，并采取相应的措施。

下面我们来详细了解一下dstat命令的使用方法。

### 安装dstat

首先，我们需要确保系统中已经安装了dstat。在Ubuntu上可以通过以下命令进行安装：

sudo apt-get install dstat

在CentOS上可以通过以下命令进行安装：

sudo yum install dstat

通过上述命令，我们将dstat安装到了系统中，现在可以开始使用它了。

### 使用dstat

dstat的使用方法相当简单。只需在终端上输入dstat命令，即可得到系统性能数据的实时监控。如下图所示：

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/52ef36b063ad4df59cd2c790fce5bcd9~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

从上述图中我们可以看到dstat提供了CPU、内存、磁盘I/O、网络流量等信息的实时监测。

dstat支持多种输出模式，可以通过命令行参数进行设置。例如，我们可以通过“-c”参数来输出CPU使用情况，如下所示：

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/941d596ec5604366a330e3dad36e60db~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

上述命令使用了“-c”参数，仅输出了CPU使用情况的信息。类似的，我们还可以使用“-m”参数查看内存使用情况，使用“-d”参数查看磁盘I/O情况，使用“-n”参数查看网络流量情况等等。

此外，dstat还提供了更加详细的输出模式。例如，我们可以使用“-g”参数来查看磁盘信息的更多细节，如下所示：

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8319b00950b8406c9f9707ab0b1a9c6f~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

上述命令使用了“-g”参数，输出了磁盘信息的更多详细数据。我们可以在输出结果中发现每个磁盘对应的读写速度、I/O请求等详细信息。

完整的dstat命令参数介绍可以通过以下命令进行查看：

dstat --help

了解了dstat命令的使用方法和注意事项之后，我们来看一些使用场景，以帮助读者更好地掌握和应用dstat命令。

### 一些案例

1.  CPU性能分析

如果我们需要了解系统中CPU占用情况的性能数据，我们可以通过以下命令来监测：

```css
dstat --cpu --top-cpu

```

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6754ccd6efa24d718eff54425015d9a5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

该命令将实时输出各个进程的CPU占用情况，并以一个实时的“top”列表形式展示。通过该命令，我们可以快速发现CPU占用率最高的进程，以便进行后续的优化和改进。

2.  磁盘IO性能分析

在处理高并发的访问请求时，磁盘I/O往往是系统性能的瓶颈之一。如果我们需要了解系统中磁盘I/O的性能数据，可以通过以下命令进行监测：

```css
dstat --disk --top-bio

```

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a3f258d8132847de807b9ccc3db0ad50~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

该命令将实时输出各个分区的磁盘IO数据，并以一个实时的“top”列表形式展示。通过该命令，我们可以快速发现磁盘I/O占用率最高的分区，以便进行后续的优化和改进。

3.  网络性能分析

如果我们需要了解系统中网络流量的性能数据，可以通过以下命令进行监测：

```css
dstat --net --tcp --udp

```

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6bc82bffc2024ea48c49331e9a286f56~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

该命令将实时输出TCP和UDP连接情况、网络流量数据等，以帮助我们分析系统中的网络性能问题，并采取相应的措施。

### 总结

通过以上介绍，我们可以看到dstat是一个非常实用的Linux系统监控工具，可以帮助我们快速定位系统性能问题，并采取相应的措施。在实际的系统管理中，我们可以根据不同的场景使用不同的参数，以得到更加精准、详细的监控数据。

### 参考文献

```less
1. Dstat – A Versatile Resource Statistics Tool. https://www.tecmint.com/dstat-a-versatile-resource-statistics-tool-for-linux/

2. Dstat. http://dag.wiee.rs/home-made/dstat/

```

分类：

[后端](/backend)

标签：

[后端](/tag/%E5%90%8E%E7%AB%AF)

文章被收录于专栏：

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/17fd1a6fa3e44021a7d5d1cdf19d8773~tplv-k3u1fbpfcp-no-mark:160:160:160:120.awebp?)

Linux实用工具

介绍一些左羊常用的Linux实用工具

订阅专栏

[安装掘金浏览器插件](https://juejin.cn/extension/?utm_source=standalone&utm_medium=post&utm_campaign=extension_promotion)

多内容聚合浏览、多引擎快捷搜索、多工具便捷提效、多模式随心畅享，你想要的，这里都有！

[前往安装](https://juejin.cn/extension/?utm_source=standalone&utm_medium=post&utm_campaign=extension_promotion)

相关小册

![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2020/6/20/172d1488323e5a18~tplv-t2oaga2asx-no-mark:420:420:300:420.awebp)

VIP

深入理解 TCP 协议：从原理到实战

[挖坑的张师傅 ![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2fa3f08a7107485f81157b296fd9d41f~tplv-k3u1fbpfcp-no-mark:0:0:0:0.awebp)
 

VIP.3 渐入佳境

![](https://lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/ffdbad884aa0e7884cbcf924226df6ce.svg)


](/user/430664257374270)

7544购买

¥24.95

¥49.9

首单券后价

首单券后价

![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/5/10/16a9d7ca96cf1e2f~tplv-t2oaga2asx-no-mark:420:420:300:420.awebp)

图解 Kafka 之实战指南

[朱小厮 ![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a3f5a3e7550645a08184e5c4247cc3d4~tplv-k3u1fbpfcp-no-mark:0:0:0:0.awebp)](/user/3808363978171566) 

4567购买

¥14.95

¥29.9

首单券后价

首单券后价

评论

![](https://lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/58aaf1326ac763d8a1054056f3b7f2ef.svg)

看完啦，

登录

分享一下感受吧～

表情

图片

Ctrl + Enter发表评论

相关推荐

*   [
    
    前端一叶子
    
    ](/user/2999123451840045)
    
    6月前
    
    [前端](/tag/%E5%89%8D%E7%AB%AF) [后端](/tag/%E5%90%8E%E7%AB%AF)
    
    [推荐10个实用的程序员开发常用工具](/post/7146940360466366501 "推荐10个实用的程序员开发常用工具")
    
    [
    
    本文已参与「新人创作礼」活动，一起开启掘金创作之路。 前言 1. 截图工具(snipaste) 官网地址 snipaste是一款截图+贴图工具，按住F1快捷键就可轻松截图，还可调整窗口大小和移动截图窗
    
    ](/post/7146940360466366501)
    
    *   2.4w
    *   283
    *   49
    
    ![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0e94881e63a644fe80847f458a7b5487~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    MacroZheng
    
    ](/user/958429871749192)
    
    1年前
    
    [后端](/tag/%E5%90%8E%E7%AB%AF) [Java](/tag/Java) [Redis](/tag/Redis)
    
    [颜值爆表！Redis官方可视化工具来啦，功能真心强大！](/post/7072537112834211847 "颜值爆表！Redis官方可视化工具来啦，功能真心强大！")
    
    [
    
    最近逛了一下Redis官方网站，发现Redis不仅推出了很多新特性，而且还发布了一款可视化工具。试用了一下感觉非常不错，最关键的是能支持RedisJSON之类的新特性，推荐给大家！
    
    ](/post/7072537112834211847)
    
    *   8.6w
    *   492
    *   87
    
    ![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/47a0e20062d340df9d1a9426d4400d94~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    CUGGZ
    
    ](/user/3544481220801815)
    
    1年前
    
    [前端](/tag/%E5%89%8D%E7%AB%AF) [JavaScript](/tag/JavaScript) [程序员](/tag/%E7%A8%8B%E5%BA%8F%E5%91%98)
    
    [33个非常实用的JavaScript一行代码，建议收藏！](/post/7025771605422768159 "33个非常实用的JavaScript一行代码，建议收藏！")
    
    [
    
    33个实用JavaScript一行代码，建议收藏！最近在国外技术社区看到了一些关于一行代码的文章，感觉很有意思，就整理了一下来分享给大家，希望对你有所帮助。
    
    ](/post/7025771605422768159)
    
    *   9.8w
    *   2202
    *   69
    
    ![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/870d6b07d5b842d6bc3c1f579bc9c67e~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    杨村长
    
    ](/user/325111174926350)
    
    10月前
    
    [前端](/tag/%E5%89%8D%E7%AB%AF) [面试](/tag/%E9%9D%A2%E8%AF%95) [Vue.js](/tag/Vue.js)
    
    [历时一个月，2.6W字！50+Vue经典面试题源码级详解，你值得收藏！](/post/7097067108663558151 "历时一个月，2.6W字！50+Vue经典面试题源码级详解，你值得收藏！")
    
    [
    
    这是村长整整花了一个月时间收集题目，亲自手写答案，录制讲解视频，汇集了50+以上经典的Vue面试题，每题我都力争做到源码级的解析，希望大家可以深入学习，如果你喜欢请务必点赞、收藏、留言支持我~
    
    ](/post/7097067108663558151)
    
    *   9.9w
    *   2408
    *   164
    
    ![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ba7d123d52ad4f6e9c907a75adaf4f4c~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    程序员老鱼
    
    ](/user/1908407914209656)
    
    1月前
    
    [掘金·日新计划](/tag/%E6%8E%98%E9%87%91%C2%B7%E6%97%A5%E6%96%B0%E8%AE%A1%E5%88%92) [ChatGPT](/tag/ChatGPT) [OpenAI](/tag/OpenAI)
    
    [ChatGPT保姆级教程，一分钟学会使用ChatGPT！](/post/7198097078005841980 "ChatGPT保姆级教程，一分钟学会使用ChatGPT！")
    
    [
    
    最近ChatGPT大火！微软退出首款ChatGPT搜索引擎，阿里等国内巨头也纷纷爆出自家产品，一夜之间，全球最大的科技公司仿佛都回到了自己年轻时的样子！ 然而，ChatGPT这么火，这么好玩的东西，国
    
    ](/post/7198097078005841980)
    
    *   30.7w
    *   309
    *   274
    
    ![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0453f8de6e4c4da1903dfa65587de65c~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    程序员依扬
    
    ](/user/3720403075993373)
    
    3年前
    
    [面试](/tag/%E9%9D%A2%E8%AF%95) [前端](/tag/%E5%89%8D%E7%AB%AF)
    
    [【1 月最新】前端 100 问：能搞懂 80% 的请把简历给我](/post/6844903885488783374 "【1 月最新】前端 100 问：能搞懂 80% 的请把简历给我")
    
    [
    
    半年时间，几千人参与，精选大厂前端面试高频 100 题，这就是「壹题」。 在 2019 年 1 月 21 日这天，「壹题」项目正式开始，在这之后每个工作日都会出一道高频面试题，主要涵盖阿里、腾讯、头条、百度、网易等大公司和常见题型。得益于大家热情参与，现在每道题都有很多答案，提…
    
    ](/post/6844903885488783374)
    
    *   63.2w
    *   11008
    *   378
    
*   [
    
    MacroZheng
    
    ](/user/958429871749192)
    
    11月前
    
    [后端](/tag/%E5%90%8E%E7%AB%AF) [Java](/tag/Java) [Spring Boot](/tag/Spring%20Boot)
    
    [解放双手！推荐一款阿里开源的低代码工具，YYDS！](/post/7088121411981541390 "解放双手！推荐一款阿里开源的低代码工具，YYDS！")
    
    [
    
    之前在我印象中低代码就是通过图形化界面来生成代码而已，其实真正的低代码把它当做一站式开发平台也不为过！最近体验了一把阿里开源的低代码工具，确实是一款面向企业级的低代码解决方案，推荐给大家！
    
    ](/post/7088121411981541390)
    
    *   12.6w
    *   1060
    *   158
    
    ![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/677eac23eddf4354b06463b5e89ac764~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    愣锤
    
    ](/user/3333374984065608)
    
    4年前
    
    [Vue.js](/tag/Vue.js) [JavaScript](/tag/JavaScript) [前端](/tag/%E5%89%8D%E7%AB%AF)
    
    [Vue 项目里戳中你痛点的问题及解决办法（更新）](/post/6844903632815521799 "Vue 项目里戳中你痛点的问题及解决办法（更新）")
    
    [
    
    最近要求使用vue进行前后端分离开发微信公众号，不断摸索踩坑之后，总结出如下几点vue项目开发中常见的问题及解决办法。如果你是vue大佬，请忽略小弟的愚见^V^ 列表进入详情页的传参问题。 列表进入详情页的传参问题。 c页面的路径为http://localhost:8080/#…
    
    ](/post/6844903632815521799)
    
    *   15.0w
    *   3739
    *   171
    
    ![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2018/7/6/1646ed05eb69e5f3~tplv-t2oaga2asx-no-mark:240:240:240:160.awebp)
    
*   [
    
    白小明
    
    ](/user/1697301683244093)
    
    4年前
    
    [HTML](/tag/HTML) [CSS](/tag/CSS) [JavaScript](/tag/JavaScript)
    
    [前端常用插件、工具类库汇总，不要重复造轮子啦！！！](/post/6844903683411410951 "前端常用插件、工具类库汇总，不要重复造轮子啦！！！")
    
    [
    
    在开发中，我们经常会将一些常用的代码块、功能块进行封装，为的是更好的复用。那么，被抽离出来独立完成功能，通过API或配置项和其他部分交互，便形成了插件。 下面这些是我在工作中积累的一些常用的前端开源插件，这里只是罗列出来，详细的用法各个插件官网或者Gayhub都有介绍。注意：往…
    
    ](/post/6844903683411410951)
    
    *   20.7w
    *   5370
    *   161
    
    ![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2018/9/24/16607a70d0cdc760~tplv-t2oaga2asx-no-mark:240:240:240:160.awebp)
    
*   [
    
    MacroZheng
    
    ](/user/958429871749192)
    
    1年前
    
    [后端](/tag/%E5%90%8E%E7%AB%AF) [Java](/tag/Java) [Linux](/tag/Linux)
    
    [官方标配！非常炫酷的 Linux 可视化管理工具，你值得拥有！](/post/7067708664651448327 "官方标配！非常炫酷的 Linux 可视化管理工具，你值得拥有！")
    
    [
    
    用了很久的CentOS 7，最近想体验一下CentOS 8。无意中发现CentOS 8内置了一款可视化管理工具\`Cockpit\`，一些常见的命令行操作它都能支持，界面炫酷且功能强大，推荐给大家！
    
    ](/post/7067708664651448327)
    
    *   2.4w
    *   133
    *   11
    
    ![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4684b23b791b4ffab5d8f9ff9d2716a1~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    狂砍2分4篮板
    
    ](/user/1239904849499911)
    
    1年前
    
    [Vue.js](/tag/Vue.js) [JavaScript](/tag/JavaScript)
    
    [新一代状态管理工具，Pinia.js 上手指南](/post/7049196967770980389 "新一代状态管理工具，Pinia.js 上手指南")
    
    [
    
    前言 Pinia.js 是新一代的状态管理器，由 Vue.js团队中成员所开发的，因此也被认为是下一代的 Vuex，即 Vuex5.x，在 Vue3.0 的项目中使用也是备受推崇。 Pinia.js
    
    ](/post/7049196967770980389)
    
    *   5.3w
    *   884
    *   185
    
    ![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/13e02cc7f656436bb9848b8b4ef63282~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    Lion
    
    ](/user/1099167361155790)
    
    2年前
    
    [Linux](/tag/Linux) [后端](/tag/%E5%90%8E%E7%AB%AF)
    
    [2万字系统总结，带你实现 Linux 命令自由？](/post/6938385978004340744 "2万字系统总结，带你实现 Linux 命令自由？")
    
    [
    
    Linux 的学习对于一个程序员的重要性是不言而喻的。前端开发相比后端开发，接触 Linux 机会相对较少，因此往往容易忽视它。但是学好它却是程序员必备修养之一。 如果本文对你有所帮助，请点个👍 吧。 作者使用的是阿里云服务器 ECS （最便宜的那种） CentOS 7.7 …
    
    ](/post/6938385978004340744)
    
    *   3.6w
    *   775
    *   40
    
*   [
    
    HelloGitHub
    
    ](/user/1574156384091320)
    
    8月前
    
    [GitHub](/tag/GitHub) [开源](/tag/%E5%BC%80%E6%BA%90) [命令行](/tag/%E5%91%BD%E4%BB%A4%E8%A1%8C)
    
    [10 款更先进的开源命令行工具](/post/7119653379587964941 "10 款更先进的开源命令行工具")
    
    [
    
    Linux 诞生于 1991 年，我们熟知的 ls、cd、ps 等命令也出生于那个年代。虽然它们都是 30 年前的产物，但是我们现在依旧每天都在用这些命令。 也许是审美疲劳又或是好奇心作祟，你可曾好奇
    
    ](/post/7119653379587964941)
    
    *   1.7w
    *   48
    *   6
    
    ![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7e172f162bf54e4589e2c665ba80648e~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    奇舞精选
    
    ](/user/4388906147515367)
    
    4年前
    
    [Google](/tag/Google) [JavaScript](/tag/JavaScript) [前端](/tag/%E5%89%8D%E7%AB%AF)
    
    [5 分钟撸一个前端性能监控工具](/post/6844903662020460552 "5 分钟撸一个前端性能监控工具")
    
    [
    
    页面性能对用户体验而言十分关键。每次重构对页面性能的提升，仅靠工程师开发设备的测试数据是没有说服力的，需要有大量的真实数据用于验证； 资源挂了、加载出现异常，不能总靠用户投诉才后知后觉，需要主动报警。 关于前端性能指标，W3C 定义了强大的 Performance API，其中…
    
    ](/post/6844903662020460552)
    
    *   4.9w
    *   1059
    *   42
    
*   [
    
    liutf
    
    ](/user/3597257774989438)
    
    4年前
    
    [GitHub](/tag/GitHub) [Google](/tag/Google) [Chrome](/tag/Chrome)
    
    [老司机的神兵利器-效率工具](/post/6844903602817859598 "老司机的神兵利器-效率工具")
    
    [
    
    快速启动应用，Windows版的神器Alfred。 快速启动应用+文件搜索+各种实用插件（计算器、翻译、网页快速访问等）。 我的最爱，没有它我几乎半残。 一开始从用altrun 然后试过Listary ，发现WOX 后，最为顺手，效率提升100%。 秒找电脑里的各种文件。与WO…
    
    ](/post/6844903602817859598)
    
    *   4.8w
    *   1213
    *   43
    
*   [
    
    前端老干部
    
    ](/user/2356967125558936)
    
    6月前
    
    [前端](/tag/%E5%89%8D%E7%AB%AF) [Vue.js](/tag/Vue.js) [JavaScript](/tag/JavaScript)
    
    [推荐16个前端必备的实用工具与网站✨](/post/7143142671920398373 "推荐16个前端必备的实用工具与网站✨")
    
    [
    
    推荐16个前端必备的实用工具与网站。一些日常工作中比较实用的软件和网站，这些网站你平时工作中大概率是会用到的，感觉不错的话可以点赞收藏🤪🤪
    
    ](/post/7143142671920398373)
    
    *   5.5w
    *   1194
    *   80
    
    ![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/977fcaa634ca4c2b972ee0e60754510c~tplv-k3u1fbpfcp-no-mark:240:240:240:160.awebp?)
    
*   [
    
    zolobdz
    
    ](/user/940837683079063)
    
    5年前
    
    [iOS开发实用技巧和工具](/post/6844903534396358663 "iOS开发实用技巧和工具")
    
    [
    
    Xcode是苹果最知名的开发工具，但并不是唯一的开发工具。Appcode就是另一款强大的iOS开发工具，用过JetBrain产品的人都深知其好处，丰富的快捷键，强大的提示功能，会用的人都说好(我说的是会用，用了两天没用明白就放弃的兄弟你是真的错过了好东西)。 但是要说明一点。只…
    
    ](/post/6844903534396358663)
    
    *   2.2w
    *   10
    *   2
    
*   [
    
    LinDaiDai\_霖呆呆
    
    ](/user/360295513463912)
    
    3年前
    
    [JavaScript](/tag/JavaScript) [Promise](/tag/Promise)
    
    [【建议星星】要就来45道Promise面试题一次爽到底(1.1w字用心整理)](/post/6844904077537574919 "【建议星星】要就来45道Promise面试题一次爽到底(1.1w字用心整理)")
    
    [
    
    你盼世界，我盼望你无bug。Hello 大家好！我是霖呆呆！ 时隔一周不见，霖呆呆我终于更新文章了，小声嘀咕说想我了... 呸... 咳咳，其实我一直在隐忍准备来一发大的好不。 这不，这一章节就是整理了45道Promise的笔试题让大家爽一爽 😁。 另外查了很多关于Promi…
    
    ](/post/6844904077537574919)
    
    *   15.1w
    *   3610
    *   489
    
    ![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2020/2/28/1708bf0e48b21309~tplv-t2oaga2asx-no-mark:240:240:240:160.awebp)
    
*   [
    
    秋天不落叶
    
    ](/user/1838039171859662)
    
    3年前
    
    [React.js](/tag/React.js)
    
    [React Hooks 详解 【近 1W 字】+ 项目实战](/post/6844903985338400782 "React Hooks 详解 【近 1W 字】+ 项目实战")
    
    [
    
    如果你在编写函数组件并意识到需要向其添加一些 state，以前的做法是必须将其它转化为 class。现在你可以直接在现有的函数组件中使用 Hooks 1. 类组件的不足 综上所述，如果不注意的话，很容易写成第三种写法，导致性能上有所损耗。 2. Hooks 优势 副作用的关注点…
    
    ](/post/6844903985338400782)
    
    *   15.6w
    *   2800
    *   107
    
*   [
    
    敖丙
    
    ](/user/4406498333825357)
    
    3年前
    
    [Java](/tag/Java) [敏捷开发](/tag/%E6%95%8F%E6%8D%B7%E5%BC%80%E5%8F%91)
    
    [《吐血整理》顶级程序员工具集](/post/6844904004716068871 "《吐血整理》顶级程序员工具集")
    
    [
    
    这期是被人才群交流里，还有很多之前网友评论强行顶出来的一期，就是让我介绍自己常用的一些工具给他们安利一下，我一听很高兴呀，帅丙我这么乐于奉献的人是吧。 千万不要白嫖，真香警告⚠️。 但是我在构思这篇文章的时候发现我贴个标题，然后发下软件信息会不会太乏味了，于是创作鬼才我呀，准备…
    
    ](/post/6844904004716068871)
    
    *   9.5w
    *   1844
    *   110
    
    ![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/11/25/16ea2da6e9ece205~tplv-t2oaga2asx-no-mark:240:240:240:160.awebp)
    

友情链接：

*   [ligerui java后台](https://backend.devrank.cn/traffic-aggregation/1194285 "ligerui java后台")
*   [python 打印换行符](https://backend.devrank.cn/traffic-aggregation/1194322 "python 打印换行符")
*   [js实现图片变灰](https://frontend.devrank.cn/traffic-aggregation/217884 "js实现图片变灰")
*   [vue 大屏模板](https://frontend.devrank.cn/traffic-aggregation/217885 "vue 大屏模板")

[![](https://p3-passport.byteimg.com/img/user-avatar/6838c75c150c97db09eb7b9d186a3f45~100x100.awebp)
](/user/1626932939607166)

[](/user/1626932939607166)[左羊 ![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ad1d5b8ec0974b0bbc14446acdd7c20d~tplv-k3u1fbpfcp-no-mark:0:0:0:0.awebp)](/user/1626932939607166) 

软件工程师

关注[

私信

](/notification/im?participantId=1626932939607166)

获得点赞  62

文章被阅读  1,765

[![](https://lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/img/sign-in.d6891e5.png)
](/user/center/signin?from=item) 

相关文章

[

Java8 Stream中如何对集合数据进行快速匹配和赋值

16点赞

 · 

0评论



](/post/7215155257172721719 "Java8 Stream中如何对集合数据进行快速匹配和赋值")[

推荐16个前端必备的实用工具与网站✨

1194点赞

 · 

80评论



](/post/7143142671920398373 "推荐16个前端必备的实用工具与网站✨")[

分享8个非常实用的Vue自定义指令

2059点赞

 · 

138评论



](/post/6906028995133833230 "分享8个非常实用的Vue自定义指令")[

最新的前端大厂面经（详解答案）

4085点赞

 · 

258评论



](/post/7004638318843412493 "最新的前端大厂面经（详解答案）")[

2万字系统总结，带你实现 Linux 命令自由？

775点赞

 · 

40评论



](/post/6938385978004340744 "2万字系统总结，带你实现 Linux 命令自由？")

目录

*   [文字首发于公众号|左羊公社](#heading-0 "文字首发于公众号|左羊公社")
    
    *   [Linux dstat命令详解](#heading-1 "Linux dstat命令详解")
        
    *   [安装dstat](#heading-2 "安装dstat")
        
    *   [使用dstat](#heading-3 "使用dstat")
        
    *   [一些案例](#heading-4 "一些案例")
        
    *   [总结](#heading-5 "总结")
        
    *   [参考文献](#heading-6 "参考文献")
        

下一篇

* * *

[【Linux实用工具】netstat命令详解及使用场景](/post/7215155257172738103 "【Linux实用工具】netstat命令详解及使用场景")

收藏成功！

已添加到「」， 点击更改

觉得还不错？

一键收藏

以便后续温习～

*   微信
    
     微信扫码分享
    
*   新浪微博
*   QQ

沉浸阅读

温馨提示

当前操作失败，如有疑问，可点击申诉

前往申诉 我知道了

![](https://lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/img/MaskGroup.13dfc4f.png)
 选择你感兴趣的技术方向

后端

前端

Android

iOS

人工智能

开发工具

代码人生

阅读

跳过

上一步

至少选择1个分类

![](https://lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/8867e249c23a7c0ea596c139befc04d7.svg)