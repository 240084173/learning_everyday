# ffmpeg库使用，undefined reference错误 - BeyondWXF的个人页面 - OSCHINA - 中文开源技术交流社区
     ffmpeg库使用，undefined reference错误 - BeyondWXF的个人页面 - OSCHINA - 中文开源技术交流社区                                                   

*   [首页](https://www.oschina.net)
*   [资讯](https://www.oschina.net/news)
*   [摸鱼](https://www.oschina.net/action/visit/ad?id=1447)
*   [专区](https://www.oschina.net/groups)
*   [问答](https://www.oschina.net/question)
*   [GOTC2023](https://www.oschina.net/action/visit/ad?id=1480)
*   开源观止
    
    [2022年 6月刊](https://www.oschina.net/action/visit/ad?id=1443) [2022年 7月刊](https://www.oschina.net/action/visit/ad?id=1454) [2022年 8月刊](https://www.oschina.net/action/visit/ad?id=1464) [2022年 9月刊](https://www.oschina.net/action/visit/ad?id=1470)
    
*   活动
    
    [开源活动](https://www.oschina.net/event) [开源创新大赛](http://bjos.oschina.net/)
    
*   [软件库](https://www.oschina.net/project)
*   [Tool](https://tool.oschina.net/)
*   [博客](https://www.oschina.net/blog)
*   [Gitee](https://gitee.com/explore?utm_source=oschina&utm_medium=link-index&utm_campaign=home)

[![](https://static.oschina.net/new-osc/img/logo_new.svg)
](https://www.oschina.net "OSCHINA")

*   [首页](https://www.oschina.net)
*   [资讯](https://www.oschina.net/news)
*   [摸鱼](https://www.oschina.net/action/visit/ad?id=1447)
*   [专区](https://www.oschina.net/groups)
*   [问答](https://www.oschina.net/question)
*   [GOTC2023](https://www.oschina.net/action/visit/ad?id=1480)
*   开源观止
    
    [2022年 6月刊](https://www.oschina.net/action/visit/ad?id=1443) [2022年 7月刊](https://www.oschina.net/action/visit/ad?id=1454) [2022年 8月刊](https://www.oschina.net/action/visit/ad?id=1464) [2022年 9月刊](https://www.oschina.net/action/visit/ad?id=1470)
    
*   活动
    
    [开源活动](https://www.oschina.net/event) [开源创新大赛](http://bjos.oschina.net/)
    
*   [软件库](https://www.oschina.net/project)
*   [Tool](https://tool.oschina.net/)
*   [博客](https://www.oschina.net/blog)
*   [Gitee](https://gitee.com/explore?utm_source=oschina&utm_medium=link-index&utm_campaign=home)

   

### OSCHINA 小程序 ——  
关注技术领域的头条文章

聚合全网技术文章，根据你的阅读喜好进行个性推荐

![](https://oscimg.oschina.net/oscnet/up-91f008637a179c217fdec464b7bad202844.jpg)

[登录](https://www.oschina.net/home/login?goto_page=https%3A%2F%2Fmy.oschina.net%2Fbeyondwxf%2Fblog%2F2248911) [注册](https://www.oschina.net/home/reg?goto_page=https%3A%2F%2Fmy.oschina.net%2Fbeyondwxf%2Fblog%2F2248911)

[开源博客](https://www.oschina.net/blog "开源博客")

[写博客](https://www.oschina.net/home/go?page=blog%2Fwrite)

   

[OSCHINA 2022 中国开源开发者问卷](https://wj.qq.com/s2/11022804/f3c0/)

![](https://oscimg.oschina.net/oscnet/up-f1efb7adeca2457da597a7e9d2ebe4d5be5.png)

[BeyondWXF的个人页面](https://my.oschina.net/beyondwxf) _/_ [工作日志](https://my.oschina.net/beyondwxf?tab=newest&catalogId=3461015) _/_

正文

[ffmpeg 库使用，undefined reference 错误](https://my.oschina.net/beyondwxf/blog/2248911)
==================================================================================

原创

[BeyondWXF](https://my.oschina.net/beyondwxf)

[工作日志](https://my.oschina.net/beyondwxf?tab=newest&catalogId=3461015)

2018/10/18 16:38

阅读数 7.2K

 [![](https://static.oschina.net/uploads/img/202008/31180726_2pwW.png)](https://www.oschina.net/group/backend "服务端") 

本文被收录于专区

[服务端](https://www.oschina.net/group/backend "服务端")

[进入专区参与更多专题讨论](https://www.oschina.net/group/backend "服务端")

ffmpeg 用 g++ 编译时的注意事项

编译时出现以下错误：

错误一：

undefined reference to \`av\_register\_all()'  
undefined reference to \`avformat\_open\_input(AVFormatContext\*\*, char const\*, AVInputFormat\*, AVDictionary\*\*)'  
undefined reference to \`avformat\_find\_stream\_info(AVFormatContext\*, AVDictionary\*\*)'  
undefined reference to \`avcodec\_find\_decoder(AVCodecID)'  
undefined reference to \`avcodec\_open2(AVCodecContext\*, AVCodec const\*, AVDictionary\*\*)'  
undefined reference to \`avcodec\_alloc\_frame()'  
undefined reference to \`avcodec\_alloc\_frame()'

解决方法：  
用 extern "C"{} 把头文件包含起来。  
extern "C"  
{  
#include <libavcodec/avcodec.h>  
#include <libavformat/avformat.h>  
#include <libswscale/swscale.h>  
}

错误二：

ffmpeg\_4.0.2/lib/libavcodec.a(tiff.o): In function \`tiff\_uncompress\_lzma':  
ffmpeg-4.0.2/libavcodec/tiff.c:398: undefined reference to \`lzma\_stream\_decoder'  
ffmpeg-4.0.2/libavcodec/tiff.c:403: undefined reference to \`lzma\_code'  
ffmpeg-4.0.2/libavcodec/tiff.c:404: undefined reference to \`lzma\_end'

解决方法：加上 - llzma 选项

参考的编译选项：

gcc push.cpp -g -I ffmpeg\_4.0.2/include -L ffmpeg\_4.0.2/lib -lavform [个人中心](https://my.oschina.net/beyondwxf/admin/bind-tel) at -lavcodec -lswresample -lavutil -pthread -lbz2  -lz -lm -llzma

展开阅读全文

[FFmpeg](https://www.oschina.net/p/ffmpeg)

© 著作权归作者所有

举报

加载中

![](https://static.oschina.net/new-osc/img/portrait.gif)

[点击引领话题📣](https://www.oschina.net/comment/blog/2248911)

取消

发布

### 作者的其它热门文章

[boost log库链接问题](https://my.oschina.net/u/2610085/blog/3054435 "boost log库链接问题")

[boost使用log库编译报错](https://my.oschina.net/u/2610085/blog/1797741 "boost使用log库编译报错")

[C++右值引用](https://my.oschina.net/u/2610085/blog/3077266 "C++右值引用")

[重载、类型转换与运算符](https://my.oschina.net/u/2610085/blog/3093379 "重载、类型转换与运算符")

打赏

0 赞

0 收藏

微信 QQ 微博

分享

### 关于作者

[

![](https://oscimg.oschina.net/oscnet/up-f6bc12640a4d2c2145545d2b4ecd874d.jpeg!/both/200x200?t=1526009331000)


](https://my.oschina.net/beyondwxf)

![](https://static.oschina.net/new-osc/img/level/lv1_small.png)

[BeyondWXF](https://my.oschina.net/beyondwxf)

程序员

关注

[私信](https://my.oschina.net/beyondwxf)

[提问](https://www.oschina.net/question/ask?user=2610085)

[

文章

29

](https://my.oschina.net/beyondwxf)

经验值

27

[

粉丝

0

](https://my.oschina.net/beyondwxf/followers)[

关注

1

](https://my.oschina.net/beyondwxf/following)

#### 作者的专辑

[全部](https://my.oschina.net/beyondwxf "查看全部专辑")

[学习日志(2)](https://my.oschina.net/beyondwxf?tab=newest&catalogId=6988170 "学习日志")

[工作日志(26)](https://my.oschina.net/beyondwxf?tab=newest&catalogId=3461015 "工作日志")

[日常记录(1)](https://my.oschina.net/beyondwxf?tab=newest&catalogId=3461016 "日常记录")

源创计划

[立即入驻](https://www.oschina.net/sharing-plan)

自媒体入驻开源社区，

获百万流量，打造个人技术品牌

### 推荐关注

换一批

[

![](https://oscimg.oschina.net/oscnet/up-227c4ec658701319416cd356bdba5a7a.jpg!/both/50x50?t=1445529259000)


](https://my.oschina.net/u/1754180 "树朾")

[树朾](https://my.oschina.net/u/1754180 "树朾")

文章 4

访问 7.5K

[

![](https://oscimg.oschina.net/oscnet/up-879f1510fb33616de9d63b1b08227796.jpeg!/both/50x50?t=1490495163000)


](https://my.oschina.net/321423 "smileNicky")

[smileNicky](https://my.oschina.net/321423 "smileNicky")

文章 1K

访问 7W

[

![](https://static.oschina.net/uploads/user/1748/3497124_50.jpeg?t=1521804783000)


](https://my.oschina.net/adailinux "阿dai学长")

[阿dai学长](https://my.oschina.net/adailinux "阿dai学长")

文章 279

访问 67.4W

[

![](https://static.oschina.net/uploads/user/2357/4714098_50.jpg?t=1603182744000)


](https://my.oschina.net/u/4714098 "九橡_小铭")

[九橡\_小铭](https://my.oschina.net/u/4714098 "九橡_小铭")

开源软件作者

[

![](https://static.oschina.net/uploads/user/461/923510_50.gif?t=1413254950000)


](https://my.oschina.net/u/923510 "悲鸣红尘")

[悲鸣红尘](https://my.oschina.net/u/923510 "悲鸣红尘")

开源软件作者

 [![](https://static.oschina.net/uploads/cooperation/blog_detail_right_sidebar_3_EKrIU.png)](https://gitee.com/activity/2022double11) 

打赏

[](https://www.oschina.net/comment/blog/2248911)

0 评论

0 收藏

0 赞

微信 QQ 微博

分享

选择专区和圈子：

取消

确定

 [![](https://oscimg.oschina.net/oscnet/up-5e130a1e4efdc9fe35229e61bbe2d0e56c9.png)
 ![](https://oscimg.oschina.net/oscnet/up-f96ba9e74eaa25d75d177560f4feeec9cd2.png)](https://wj.qq.com/s2/11022804/f3c0/) 

#### OSCHINA 社区

[关于我们](https://www.oschina.net/home/aboutosc) [联系我们](https://www.oschina.net/home/aboutosc) [加入我们](https://www.oschina.net/news/131099/oschina-hiring) [合作伙伴](https://www.oschina.net/home/aboutosc#partners) [Open API](https://www.oschina.net/openapi)

#### 在线工具

[Gitee.com](https://gitee.com/?utm_source=oschina&utm_medium=link-bottom&utm_campaign=home) [企业研发管理](https://gitee.com/enterprises?utm_source=oschina&utm_medium=link-bottom&utm_campaign=enterprises) [CopyCat-代码克隆检测](https://copycat.gitee.com/?utm_source=oschina&utm_medium=link-bottom&utm_campaign=copycat) [实用在线工具](https://tool.oschina.net) [国家反诈中心APP下载](https://oscimg.oschina.net/oscnet/up-82a1d21cdcbd86bf819ffd854dc0f1c6d72.png)

#### 攻略

[项目运营](https://www.oschina.net/question/2918182_2319406) [Awesome 软件（持续更新中）](https://my.oschina.net/u/4252687/blog/5568509)

#### QQ群

 [![](https://static.oschina.net/new-osc/img/qq_qrcode_2_new.png)](https://jq.qq.com/?_wv=1027&k=rfiPgVgE) 

[530688128](https://jq.qq.com/?_wv=1027&k=rfiPgVgE)

#### 公众号

![](https://static.oschina.net/new-osc/img/wechat_qrcode.jpg?t=1484694603000)

#### 视频号

![](https://oscimg.oschina.net/oscnet/up-7f546da372c31b5421fedc29f7c202ab2c4.JPEG)

### OSCHINA 小程序

聚合全网技术文章，根据你的阅读喜好进行个性推荐

OSC小程序

![](https://oscimg.oschina.net/oscnet/up-91f008637a179c217fdec464b7bad202844.jpg)

©OSCHINA(OSChina.NET)

工信部

[开源软件推进联盟](http://www.copu.org.cn/ "开源软件推进联盟")

指定官方社区

[社区规范](https://www.oschina.net/question/1_2326668 "OSCHINA 社区规范")

深圳市奥思网络科技有限公司版权所有

[粤ICP备12009483号](http://beian.miit.gov.cn/)

![](https://oscimg.oschina.net/oscnet/up-02f2706a81344119fb5cdcdda304068f2e0.png)
 ![](https://oscimg.oschina.net/oscnet/up-e77d060131d9b392981650ec7beb614554f.JPEG)

![](https://static.oschina.net/new-osc/img/icon/back-to-top.svg)

顶部