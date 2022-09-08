# 如何迭代pandas dataframe的行 - bonelee - 博客园
        如何迭代pandas dataframe的行 - bonelee - 博客园          

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
](https://www.cnblogs.com/bonelee/) 

[将者，智、信、仁、勇、严也。](https://www.cnblogs.com/bonelee/)
==================================================

Hi，我是李智华，华为-安全AI算法专家，欢迎来到安全攻防对抗的有趣世界。
-------------------------------------

*   [博客园](https://www.cnblogs.com/)
*   [首页](https://www.cnblogs.com/bonelee/)
*   [新随笔](https://i.cnblogs.com/EditPosts.aspx?opt=1)
*   [联系](https://msg.cnblogs.com/send/bonelee)
*   [订阅](javascript:void(0))
*   [管理](https://i.cnblogs.com/)

随笔 - 2457 文章 - 0 评论 - 883 阅读 - 728万

[如何迭代pandas dataframe的行](https://www.cnblogs.com/bonelee/p/9732761.html)
========================================================================

from:https://blog.csdn.net/tanzuozhev/article/details/76713387

How to iterate over rows in a DataFrame in Pandas-DataFrame按行迭代
---------------------------------------------------------------

[https://stackoverflow.com/questions/16476924/how-to-iterate-over-rows-in-a-dataframe-in-pandas](https://stackoverflow.com/questions/16476924/how-to-iterate-over-rows-in-a-dataframe-in-pandas)

[http://stackoverflow.com/questions/7837722/what-is-the-most-efficient-way-to-loop-through-dataframes-with-pandas](http://stackoverflow.com/questions/7837722/what-is-the-most-efficient-way-to-loop-through-dataframes-with-pandas)

在对DataFrame进行操作时，我们不可避免的需要逐行查看或操作数据，那么有什么高效、快捷的方法呢？

### index序号索引

```null
import pandas as pd
inp = [{'c1':10, 'c2':100}, {'c1':11,'c2':110}, {'c1':12,'c2':120}]
df = pd.DataFrame(inp)
for x in xrange(len(df.index)):
    print df['c1'].iloc[x]
```

  

这似乎是最常规的办法，而且可以在迭代的过程中对DataFrame进行操作。

### enumerate

```null
for i, row in enumerate(df.values):
    index= df.index[i]
    print row
```

  

df.values 是 numpy.ndarray 类型  
这里 i 是index的序号， row是numpy.ndarray类型。

### iterrows

[https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.iterrows.html](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.iterrows.html)

```null
import pandas as pd
inp = [{'c1':10, 'c2':100}, {'c1':11,'c2':110}, {'c1':12,'c2':120}]
df = pd.DataFrame(inp)

for index, row in df.iterrows():
    print row['c1'], row['c2']

#10 100
#11 110
#12 120
```

  

df.iterrows() 的每次迭代都是一个`tuple`类型,包含了index和每行的数据。

1.  采用iterrows的方法，得到的 row 是一个Series，DataFrame的dtypes不会被保留。
2.  返回的Series只是一个原始DataFrame的复制，不可以对原始DataFrame进行修改；

### itertuples

[http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.itertuples.html](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.itertuples.html)

```null
import pandas as pd
inp = [{'c1':10, 'c2':100}, {'c1':11,'c2':110}, {'c1':12,'c2':120}]
df = pd.DataFrame(inp)

for row in df.itertuples():
    # print row[0], row[1], row[2] 等同于
    print row.Index, row.c1, row.c2
```

  

itertuples 返回的是一个 pandas.core.frame.Pandas 类型。

普遍认为itertuples 比 iterrows的速度要快。

### zip / itertools.izip

zip 和 itertools.izip的用法是相似的， 但是zip返回一个list，而izip返回一个迭代器。 如果数据量很大，zip的性能不及izip

```null
from itertools import izip
import pandas as pd
inp = [{'c1':10, 'c2':100}, {'c1':11,'c2':110}, {'c1':12,'c2':120}]
df = pd.DataFrame(inp)

for row in izip(df.index, df['c1'], df['c2']):
    print row
```

  

### 时间测评

```null
import time
from numpy.random import randn

df = pd.DataFrame({'a': randn(100000), 'b': randn(100000)})

time_stat = []

# range(index)
test_list = []
t = time.time()
for r in xrange(len(df)):
    test_list.append((df.index[r], df.iloc[r,0], df.iloc[r,1]))
time_stat.append(time.time()-t)

# enumerate
test_list = []
t = time.time()
for i, r in enumerate(df.values):
    test_list.append((df.index[i], r[0], r[1]))
time_stat.append(time.time()-t)

# iterrows
test_list = []
t = time.time()
for i,r in df.iterrows():
    test_list.append((df.index[i], r['a'], r['b']))
time_stat.append(time.time()-t)

#itertuples
test_list = []
t = time.time()
for ir in df.itertuples():
    test_list.append((ir[0], ir[1], ir[2]))    
time_stat.append(time.time()-t)

# zip
test_list = []
t = time.time()
for r in zip(df.index, df['a'], df['b']):
    test_list.append((r[0], r[1], r[2]))
time_stat.append(time.time()-t)

# izip
test_list = []
t = time.time()
from itertools import izip
for r in izip(df.index, df['a'], df['b']):
    test_list.append((r[0], r[1], r[2]))
time_stat.append(time.time()-t)

time_df = pd.DataFrame({'items':['range(index)', 'enumerate',  'iterrows', 'itertuples' , 'zip', 'izip'], 'time':time_stat})

time_df.sort_values('time')


items   time
5   izip    0.034869
4   zip 0.040440
3   itertuples  0.072604
1   enumerate   0.174094
2   iterrows    4.026293
0   range(index)    21.921407
```

可以发现在时间花销上， izip > zip > itertuples > enumerate > iterrows > range(index)

标签: [python](https://www.cnblogs.com/bonelee/tag/python/)

[好文要顶](javascript:void(0);) [关注我](javascript:void(0);) [收藏该文](javascript:void(0);) [![](https://common.cnblogs.com/images/icon_weibo_24.png)
](javascript:void(0); "分享至新浪微博") [![](https://common.cnblogs.com/images/wechat.png)
](javascript:void(0); "分享至微信")

[![](https://pic.cnblogs.com/face/1011569/20161218000118.png)
](https://home.cnblogs.com/u/bonelee/)

[bonelee](https://home.cnblogs.com/u/bonelee/)  
[粉丝 - 698](https://home.cnblogs.com/u/bonelee/followers/) [关注 - 1](https://home.cnblogs.com/u/bonelee/followees/)  

[+加关注](javascript:void(0);)

1

0

[«](https://www.cnblogs.com/bonelee/p/9728663.html) 上一篇： [风控用户识别方法](https://www.cnblogs.com/bonelee/p/9728663.html "发布于 2018-09-30 11:15")  
[»](https://www.cnblogs.com/bonelee/p/9798591.html) 下一篇： [ES 分布式搜索](https://www.cnblogs.com/bonelee/p/9798591.html "发布于 2018-10-16 16:03")

posted @ 2018-09-30 17:29  [bonelee](https://www.cnblogs.com/bonelee/)  阅读(13094)  评论(0)  [编辑](https://i.cnblogs.com/EditPosts.aspx?postid=9732761)  [收藏](javascript:void(0))  [举报](javascript:void(0))

[刷新评论](javascript:void(0);)[刷新页面](#)[返回顶部](#top)

登录后才能查看或发表评论，立即 [登录](javascript:void(0);) 或者 [逛逛](https://www.cnblogs.com/) 博客园首页

[【推荐】云安全践行者：亚马逊云科技如何打好“安全”牌？](https://www.cnblogs.com/cmt/p/16647139.html)  
[【推荐】腾讯云多款云产品1折起，买云服务器送免费机器](https://curl.qcloud.com/k19RDMHo)  
[【推荐】下一步，敏捷！云可达科技SpecDD敏捷开发专区](https://brands.cnblogs.com/specdd)  

**编辑推荐：**   
· [有意思的水平横向溢出滚动](https://www.cnblogs.com/coco1s/p/16663752.html)  
· [没有二十年功力，写不出Thread.sleep(0)这一行“看似无用”的代码！](https://www.cnblogs.com/thisiswhy/p/16657667.html)  
· [CPU 流水线与指令乱序执行](https://www.cnblogs.com/chanmufeng/p/16658844.html)  
· [\[WPF\] 使用 HandyControl 的 CirclePanel 画出表盘刻度](https://www.cnblogs.com/dino623/p/16471012.html)  
· [踩坑 Windows 服务来宿主 .NET 程序](https://www.cnblogs.com/kklldog/p/host-net-on-windows-service.html)  

**最新新闻**：  
· [所有VR的厂商同样都在悄悄的做AR，但是不一定所有的AR厂商都会去做VR](//news.cnblogs.com/n/727922/)  
· [妙！苹果把iPhone 14 Pro的槽点做成了最大亮点](//news.cnblogs.com/n/727921/)  
· [RISC-V要上天！NASA选它做下一代航天计算芯片](//news.cnblogs.com/n/727920/)  
· [华为机皇回归！变4G的Mate 50，能否与iPhone一战？](//news.cnblogs.com/n/727919/)  
· [英伟达被禁的A100芯片，清华、中科院都曾斥巨资购买](//news.cnblogs.com/n/727918/)  
» [更多新闻...](https://news.cnblogs.com/ "IT 新闻")

### 公告

昵称： [bonelee](https://home.cnblogs.com/u/bonelee/)  
园龄： [6年](https://home.cnblogs.com/u/bonelee/ "入园时间：2016-08-19")  
粉丝： [698](https://home.cnblogs.com/u/bonelee/followers/)  
关注： [1](https://home.cnblogs.com/u/bonelee/followees/)

[+加关注](javascript:void(0))

| 
| [<](javascript:void(0);) | 2022年9月 | [\>](javascript:void(0);) | |
| 日 | 一 | 二 | 三 | 四 | 五 | 六 |
| 28 | 29 | 30 | 31 | 1 | 2 | 3 |
| 4 | [5](https://www.cnblogs.com/bonelee/archive/2022/09/05.html) | 6 | 7 | 8 | 9 | 10 |
| 11 | 12 | 13 | 14 | 15 | 16 | 17 |
| 18 | 19 | 20 | 21 | 22 | 23 | 24 |
| 25 | 26 | 27 | 28 | 29 | 30 | 1 |
| 2 | 3 | 4 | 5 | 6 | 7 | 8 |

### 搜索

 

 

### 常用链接

*   [我的随笔](https://www.cnblogs.com/bonelee/p/ "我的博客的随笔列表")
*   [我的评论](https://www.cnblogs.com/bonelee/MyComments.html "我的发表过的评论列表")
*   [我的参与](https://www.cnblogs.com/bonelee/OtherPosts.html "我评论过的随笔列表")
*   [最新评论](https://www.cnblogs.com/bonelee/comments "我的博客的评论列表")
*   [我的标签](https://www.cnblogs.com/bonelee/tag/ "我的博客的标签列表")

### 我的标签

*   [安全分析(993)](https://www.cnblogs.com/bonelee/tag/%E5%AE%89%E5%85%A8%E5%88%86%E6%9E%90/)
*   [机器学习(233)](https://www.cnblogs.com/bonelee/tag/%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0/)
*   [算法(183)](https://www.cnblogs.com/bonelee/tag/%E7%AE%97%E6%B3%95/)
*   [leetcode(164)](https://www.cnblogs.com/bonelee/tag/leetcode/)
*   [python(151)](https://www.cnblogs.com/bonelee/tag/python/)
*   [数据库(122)](https://www.cnblogs.com/bonelee/tag/%E6%95%B0%E6%8D%AE%E5%BA%93/)
*   [elasticsearch(116)](https://www.cnblogs.com/bonelee/tag/elasticsearch/)
*   [其他(95)](https://www.cnblogs.com/bonelee/tag/%E5%85%B6%E4%BB%96/)
*   [搜索引擎(85)](https://www.cnblogs.com/bonelee/tag/%E6%90%9C%E7%B4%A2%E5%BC%95%E6%93%8E/)
*   [spark(75)](https://www.cnblogs.com/bonelee/tag/spark/)
*   [更多](https://www.cnblogs.com/bonelee/tag/)

### 随笔档案

*   [2022年9月(3)](https://www.cnblogs.com/bonelee/archive/2022/09.html)
*   [2022年8月(28)](https://www.cnblogs.com/bonelee/archive/2022/08.html)
*   [2022年7月(40)](https://www.cnblogs.com/bonelee/archive/2022/07.html)
*   [2022年6月(48)](https://www.cnblogs.com/bonelee/archive/2022/06.html)
*   [2022年5月(41)](https://www.cnblogs.com/bonelee/archive/2022/05.html)
*   [2022年4月(27)](https://www.cnblogs.com/bonelee/archive/2022/04.html)
*   [2022年3月(55)](https://www.cnblogs.com/bonelee/archive/2022/03.html)
*   [2022年2月(83)](https://www.cnblogs.com/bonelee/archive/2022/02.html)
*   [2022年1月(16)](https://www.cnblogs.com/bonelee/archive/2022/01.html)
*   [2021年12月(5)](https://www.cnblogs.com/bonelee/archive/2021/12.html)
*   [2021年11月(10)](https://www.cnblogs.com/bonelee/archive/2021/11.html)
*   [2021年10月(8)](https://www.cnblogs.com/bonelee/archive/2021/10.html)
*   [2021年9月(17)](https://www.cnblogs.com/bonelee/archive/2021/09.html)
*   [2021年8月(42)](https://www.cnblogs.com/bonelee/archive/2021/08.html)
*   [2021年7月(29)](https://www.cnblogs.com/bonelee/archive/2021/07.html)
*   [2021年6月(40)](https://www.cnblogs.com/bonelee/archive/2021/06.html)
*   [2021年5月(47)](https://www.cnblogs.com/bonelee/archive/2021/05.html)
*   [2021年4月(20)](https://www.cnblogs.com/bonelee/archive/2021/04.html)
*   [2021年3月(13)](https://www.cnblogs.com/bonelee/archive/2021/03.html)
*   [2021年2月(15)](https://www.cnblogs.com/bonelee/archive/2021/02.html)
*   [2021年1月(38)](https://www.cnblogs.com/bonelee/archive/2021/01.html)
*   [2020年12月(13)](https://www.cnblogs.com/bonelee/archive/2020/12.html)
*   [2020年11月(14)](https://www.cnblogs.com/bonelee/archive/2020/11.html)
*   [2020年10月(28)](https://www.cnblogs.com/bonelee/archive/2020/10.html)
*   [2020年9月(18)](https://www.cnblogs.com/bonelee/archive/2020/09.html)
*   [2020年8月(4)](https://www.cnblogs.com/bonelee/archive/2020/08.html)
*   [2020年7月(8)](https://www.cnblogs.com/bonelee/archive/2020/07.html)
*   [2020年6月(11)](https://www.cnblogs.com/bonelee/archive/2020/06.html)
*   [2020年5月(14)](https://www.cnblogs.com/bonelee/archive/2020/05.html)
*   [2020年4月(22)](https://www.cnblogs.com/bonelee/archive/2020/04.html)
*   [2020年3月(49)](https://www.cnblogs.com/bonelee/archive/2020/03.html)
*   [2020年2月(4)](https://www.cnblogs.com/bonelee/archive/2020/02.html)
*   [2020年1月(2)](https://www.cnblogs.com/bonelee/archive/2020/01.html)
*   [2019年12月(13)](https://www.cnblogs.com/bonelee/archive/2019/12.html)
*   [2019年11月(26)](https://www.cnblogs.com/bonelee/archive/2019/11.html)
*   [2019年10月(19)](https://www.cnblogs.com/bonelee/archive/2019/10.html)
*   [2019年9月(21)](https://www.cnblogs.com/bonelee/archive/2019/09.html)
*   [2019年8月(17)](https://www.cnblogs.com/bonelee/archive/2019/08.html)
*   [2019年7月(25)](https://www.cnblogs.com/bonelee/archive/2019/07.html)
*   [2019年6月(13)](https://www.cnblogs.com/bonelee/archive/2019/06.html)
*   [2019年5月(15)](https://www.cnblogs.com/bonelee/archive/2019/05.html)
*   [2019年4月(16)](https://www.cnblogs.com/bonelee/archive/2019/04.html)
*   [2019年3月(7)](https://www.cnblogs.com/bonelee/archive/2019/03.html)
*   [2019年2月(8)](https://www.cnblogs.com/bonelee/archive/2019/02.html)
*   [2019年1月(14)](https://www.cnblogs.com/bonelee/archive/2019/01.html)
*   [2018年12月(13)](https://www.cnblogs.com/bonelee/archive/2018/12.html)
*   [2018年11月(34)](https://www.cnblogs.com/bonelee/archive/2018/11.html)
*   [2018年10月(28)](https://www.cnblogs.com/bonelee/archive/2018/10.html)
*   [2018年9月(28)](https://www.cnblogs.com/bonelee/archive/2018/09.html)
*   [2018年8月(16)](https://www.cnblogs.com/bonelee/archive/2018/08.html)
*   [2018年7月(38)](https://www.cnblogs.com/bonelee/archive/2018/07.html)
*   [2018年6月(62)](https://www.cnblogs.com/bonelee/archive/2018/06.html)
*   [2018年5月(85)](https://www.cnblogs.com/bonelee/archive/2018/05.html)
*   [2018年4月(66)](https://www.cnblogs.com/bonelee/archive/2018/04.html)
*   [2018年3月(112)](https://www.cnblogs.com/bonelee/archive/2018/03.html)
*   [2018年2月(33)](https://www.cnblogs.com/bonelee/archive/2018/02.html)
*   [2018年1月(46)](https://www.cnblogs.com/bonelee/archive/2018/01.html)
*   [2017年12月(36)](https://www.cnblogs.com/bonelee/archive/2017/12.html)
*   [2017年11月(81)](https://www.cnblogs.com/bonelee/archive/2017/11.html)
*   [2017年10月(25)](https://www.cnblogs.com/bonelee/archive/2017/10.html)
*   [2017年9月(35)](https://www.cnblogs.com/bonelee/archive/2017/09.html)
*   [2017年8月(41)](https://www.cnblogs.com/bonelee/archive/2017/08.html)
*   [2017年7月(53)](https://www.cnblogs.com/bonelee/archive/2017/07.html)
*   [2017年6月(40)](https://www.cnblogs.com/bonelee/archive/2017/06.html)
*   [2017年5月(76)](https://www.cnblogs.com/bonelee/archive/2017/05.html)
*   [2017年4月(50)](https://www.cnblogs.com/bonelee/archive/2017/04.html)
*   [2017年3月(92)](https://www.cnblogs.com/bonelee/archive/2017/03.html)
*   [2017年2月(111)](https://www.cnblogs.com/bonelee/archive/2017/02.html)
*   [2017年1月(107)](https://www.cnblogs.com/bonelee/archive/2017/01.html)
*   [2016年12月(80)](https://www.cnblogs.com/bonelee/archive/2016/12.html)
*   [2016年11月(38)](https://www.cnblogs.com/bonelee/archive/2016/11.html)
*   [2016年10月(11)](https://www.cnblogs.com/bonelee/archive/2016/10.html)
*   [2016年9月(3)](https://www.cnblogs.com/bonelee/archive/2016/09.html)
*   [2016年8月(3)](https://www.cnblogs.com/bonelee/archive/2016/08.html)
*   [更多](javascript:void(0))

### [阅读排行榜](https://www.cnblogs.com/bonelee/most-viewed)

*   [1\. GAN的原理入门(188806)](https://www.cnblogs.com/bonelee/p/9166084.html)
*   [2\. sklearn的train\_test\_split，果然很好用啊！(168341)](https://www.cnblogs.com/bonelee/p/8036024.html)
*   [3\. TSNE——目前最好的降维方法(123465)](https://www.cnblogs.com/bonelee/p/7849867.html)
*   [4\. npm使用国内淘宝镜像的方法(99652)](https://www.cnblogs.com/bonelee/p/9995550.html)
*   [5\. 暴力破解攻击工具汇总——字典很关键，肉鸡也关键(82135)](https://www.cnblogs.com/bonelee/p/9322684.html)

### [评论排行榜](https://www.cnblogs.com/bonelee/most-commented)

*   [1\. CC 攻击检测研究现状(45)](https://www.cnblogs.com/bonelee/p/9205313.html)
*   [2\. 网络流量预测 国内外研究现状【见评论】——传统的ARIMA、HMM模型，目前LSTM、GRU、CNN应用较多，貌似小波平滑预处理步骤非常关键(43)](https://www.cnblogs.com/bonelee/p/9441149.html)
*   [3\. 信令风暴研究现状总结(40)](https://www.cnblogs.com/bonelee/p/9288978.html)
*   [4\. ES业界优秀实践案例汇总(28)](https://www.cnblogs.com/bonelee/p/7895189.html)
*   [5\. 国外DDoS产品的一些调研—— Akamai Arbor Networks Cloudflare DOSarrest F5 Fastly Imperva Link11 Neustar Nexusguard Oracle (Dyn) Radware Verisign(22)](https://www.cnblogs.com/bonelee/p/9220016.html)

### [推荐排行榜](https://www.cnblogs.com/bonelee/most-liked)

*   [1\. GAN的原理入门(18)](https://www.cnblogs.com/bonelee/p/9166084.html)
*   [2\. python 循环高级用法 \[expression for x in X \[if condition\] for y in Y \[if condition\] ... for n in N \[if condition\] \]按照从左至右的顺序，分别是外层循环到内层循环(13)](https://www.cnblogs.com/bonelee/p/8545263.html)
*   [3\. sklearn的train\_test\_split，果然很好用啊！(10)](https://www.cnblogs.com/bonelee/p/8036024.html)
*   [4\. npm使用国内淘宝镜像的方法(7)](https://www.cnblogs.com/bonelee/p/9995550.html)
*   [5\. SENet（Squeeze-and-Excitation Networks）算法笔记---通过学习的方式来自动获取到每个特征通道的重要程度，然后依照这个重要程度去提升有用的特征并抑制对当前任务用处不大的特征(7)](https://www.cnblogs.com/bonelee/p/9030092.html)

### [最新评论](https://www.cnblogs.com/bonelee/comments)

*   [1\. Re:我的sysmon配置，默认配置就看到了进程采集，其他数据采集还是要配置下的](https://www.cnblogs.com/bonelee/p/16165337.html)
*   配置文件：  
    
*   \--bonelee
*   [2\. Re:人工智能 kmeans和som的简单比较——线性可分的数据还可以，但都不擅长处理圆分割数据，因为用的欧几里得距离？](https://www.cnblogs.com/bonelee/p/15107908.html)
*   请问最后一个例子中 KPCA和kmeans是怎么结合的？是否可以理解成： 对数据线先用核函数升维，然后对升维后的数据进行kmeans聚类（但不进行PCA）？
    
*   \--yhlc
*   [3\. Re:Windows 提权方式总结](https://www.cnblogs.com/bonelee/p/16619497.html)
*   \[2022-08-26 15:35:18.970\]\[Info\] \[16004\] \[HIPS INPUT\]: Event name is ProcessStart, \[eventTime\] 166149...
*   \--bonelee
*   [4\. Re:元学习MAML——要解决的问题是给你一堆猫狗图片（训练样本较多），然后给你一类黑天鹅图谱（样本少），让你训练一个模型，能够泛化能力好，识别猫狗和黑天鹅](https://www.cnblogs.com/bonelee/p/15078409.html)
*   1m6jruv\_gaMTQ3MjQ3MTY2Ny4xNjQ1NTk4MDcx\_ga\_53KB74YDZR\*MTY2MTQ4MzYwNy4xNy4wLjE2NjE0ODM2MDcuNjAuMC4w&\_g...
*   \--bonelee
*   [5\. Re:元学习MAML——要解决的问题是给你一堆猫狗图片（训练样本较多），然后给你一类黑天鹅图谱（样本少），让你训练一个模型，能够泛化能力好，识别猫狗和黑天鹅](https://www.cnblogs.com/bonelee/p/15078409.html)
*   检测针对HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\WINDOWS\\CURRENTVERSION\\POLICIES\\SYSTEM中ENABLELUA设置为0 WRITE...
*   \--bonelee

Copyright © 2022 bonelee  
Powered by .NET 6 on Kubernetes