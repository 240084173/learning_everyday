# 代码详解Python多线程、多进程、协程 - 刘早起的个人空间 - OSCHINA - 中文开源技术交流社区
     代码详解Python多线程、多进程、协程 - 刘早起的个人空间 - OSCHINA - 中文开源技术交流社区                                                  

*   [首页](https://www.oschina.net)
*   [资讯](https://www.oschina.net/news)
*   [摸鱼](https://www.oschina.net/action/visit/ad?id=1447)
*   [专区](https://www.oschina.net/groups)
*   [问答](https://www.oschina.net/question)
*   开源观止
    
    [2022年 6月刊](https://www.oschina.net/action/visit/ad?id=1443) [2022年 7月刊](https://www.oschina.net/action/visit/ad?id=1454) [2022年 8月刊](https://www.oschina.net/action/visit/ad?id=1464) [2022年 9月刊](https://www.oschina.net/action/visit/ad?id=1470)
    
*   [活动](https://www.oschina.net/event)
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
*   开源观止
    
    [2022年 6月刊](https://www.oschina.net/action/visit/ad?id=1443) [2022年 7月刊](https://www.oschina.net/action/visit/ad?id=1454) [2022年 8月刊](https://www.oschina.net/action/visit/ad?id=1464) [2022年 9月刊](https://www.oschina.net/action/visit/ad?id=1470)
    
*   [活动](https://www.oschina.net/event)
*   [软件库](https://www.oschina.net/project)
*   [Tool](https://tool.oschina.net/)
*   [博客](https://www.oschina.net/blog)
*   [Gitee](https://gitee.com/explore?utm_source=oschina&utm_medium=link-index&utm_campaign=home)

   

### OSCHINA 小程序 ——  
关注技术领域的头条文章

聚合全网技术文章，根据你的阅读喜好进行个性推荐

![](https://oscimg.oschina.net/oscnet/up-91f008637a179c217fdec464b7bad202844.jpg)

[登录](https://www.oschina.net/home/login?goto_page=https%3A%2F%2Fmy.oschina.net%2Fu%2F4579171%2Fblog%2F4366709) [注册](https://www.oschina.net/home/reg?goto_page=https%3A%2F%2Fmy.oschina.net%2Fu%2F4579171%2Fblog%2F4366709)

[开源博客](https://www.oschina.net/blog "开源博客")

[写博客](https://www.oschina.net/home/go?page=blog%2Fwrite)

   

[刘早起的个人空间](https://my.oschina.net/u/4579171) _/_ [早起Python](https://my.oschina.net/u/4579171?tab=newest&catalogId=7031888) _/_

正文

[代码详解 Python 多线程、多进程、协程](https://my.oschina.net/u/4579171/blog/4366709)
=======================================================================

[刘早起](https://my.oschina.net/u/4579171)

[早起Python](https://my.oschina.net/u/4579171?tab=newest&catalogId=7031888)

2020/04/06 11:09

阅读数 15

 [![](https://static.oschina.net/uploads/img/202008/31180731_vRmf.png)](https://www.oschina.net/group/skill "开发技能") 

本文被收录于专区

[开发技能](https://www.oschina.net/group/skill "开发技能")

[进入专区参与更多专题讨论](https://www.oschina.net/group/skill "开发技能")

[正在直播： LF AI 基金会主办首届 AICON 2022 >>>![](https://www.oschina.net/img/hot3.png)
](http://aicon.osctraining.com/)

点击上方 “**早起 Python**”，关注并星标公众号

和我一起玩 Python

![](https://oscimg.oschina.net/oscnet/3ee3b97952121254d3c3f63fd563d03775e.jpg)

一、前言

![](https://oscimg.oschina.net/oscnet/5cf07dc92882ceddaaaae114081738834c6.png)

很多时候我们写了一个爬虫，实现了需求后会发现了很多值得改进的地方，其中很重要的一点就是爬取速度。本文就通过代码讲解如何使用**多进程、多线程、协程**来提升爬取速度。注意：我们不深入介绍理论和原理，一切都在代码中。

  

二、同步

![](https://oscimg.oschina.net/oscnet/5cf07dc92882ceddaaaae114081738834c6.png)

首先我们写一个简化的爬虫，对各个功能细分，有意识进行函数式编程。下面代码的目的是访问 300 次百度页面并返回状态码，其中 `parse_1` 函数可以设定循环次数，每次循环将当前循环数（从 0 开始）和 url 传入 `parse_2` 函数。

```
import requests  
  
def parse_1():  
    url = 'https://www.baidu.com'  
    for i in range(300):  
        parse_2(url)  
  
defparse_2(url):  
    response = requests.get(url)  
    print(response.status_code)  
  
if __name__ == '__main__':  
    parse_1()
```

**性能的消耗主要在 IO 请求中，当单进程单线程模式下请求 URL 时必然会引起等待**

示例代码就是典型的串行逻辑， `parse_1` 将 url 和循环数传递给 `parse_2` ， `parse_2` 请求并返回状态码后 `parse_1` 继续迭代一次，重复之前步骤

  

三、多线程

![](https://oscimg.oschina.net/oscnet/5cf07dc92882ceddaaaae114081738834c6.png)

因为 CPU 在执行程序时每个时间刻度上只会存在一个线程，因此多线程实际上提高了进程的使用率从而提高了 CPU 的使用率

实现多线程的库有很多，这里用 `concurrent.futures` 中的 `ThreadPoolExecutor` 来演示。介绍 `ThreadPoolExecutor` 库是因为它相比其他库代码更简洁

  

#### **为了方便说明问题，下面代码中如果是新增加的部分，代码行前会加上 > 符号便于观察说明问题，实际运行需要去掉**

```
import requests  
> from concurrent.futures import ThreadPoolExecutor  
  
def parse_1():  
    url = 'https://www.baidu.com'  
    # 建立线程池  
    > pool = ThreadPoolExecutor(6)  
    for i in range(300):  
        > pool.submit(parse_2, url)  
    > pool.shutdown(wait=True)  
  
def parse_2(url):  
    response = requests.get(url)  
    print(response.status_code)  
  
if __name__ == '__main__':  
    parse_1()
```

跟同步相对的就是**异步**。异步就是彼此独立，在等待某事件的过程中继续做自己的事，不需要等待这一事件完成后再工作。线程就是实现异步的一个方式，也就是说多线程是异步处理异步就意味着不知道处理结果，有时候我们需要了解处理结果，就可以采用**回调**

```
import requests  
from concurrent.futures import ThreadPoolExecutor  
  
# 增加回调函数  
> def callback(future):  
    > print(future.result())  
  
def parse_1():  
    url = 'https://www.baidu.com'  
    pool = ThreadPoolExecutor(6)  
    for i in range(300):  
        > results = pool.submit(parse_2, url)  
        # 回调的关键步骤  
        > results.add_done_callback(callback)  
    pool.shutdown(wait=True)  
  
def parse_2(url):  
    response = requests.get(url)  
    print(response.status_code)  
  
if __name__ == '__main__':  
    parse_1()
```

Python 实现多线程有一个无数人诟病的 **GIL (全局解释器锁)**，但多线程对于爬取网页这种多数属于 IO 密集型的任务依旧很合适。

  

四、多进程

![](https://oscimg.oschina.net/oscnet/5cf07dc92882ceddaaaae114081738834c6.png)

  

多进程用两个方法实现： `ProcessPoolExecutor` 和 `multiprocessing`

###### **1\. ProcessPoolExecutor**

和实现多线程的 `ThreadPoolExecutor` 类似

```
import requests  
> from concurrent.futures import ProcessPoolExecutor  
  
def parse_1():  
    url = 'https://www.baidu.com'  
    # 建立线程池  
    > pool = ProcessPoolExecutor(6)  
    for i in range(300):  
        > pool.submit(parse_2, url)  
    > pool.shutdown(wait=True)  
  
def parse_2(url):  
    response = requests.get(url)  
    print(response.status_code)  
  
if __name__ == '__main__':  
    parse_1()
```

可以看到改动了两次类名，代码依旧很简洁，同理也可以添加**回调**函数

```
import requests  
from concurrent.futures import ProcessPoolExecutor  
  
> defcallback(future):  
    > print(future.result())  
  
defparse_1():  
    url = 'https://www.baidu.com'  
    pool = ProcessPoolExecutor(6)  
    for i in range(300):  
        > results = pool.submit(parse_2, url)  
        > results.add_done_callback(callback)  
    pool.shutdown(wait=True)  
  
defparse_2(url):  
    response = requests.get(url)  
    print(response.status_code)  
  
if __name__ == '__main__':  
    parse_1()
```

##### 

##### **2\. multiprocessing**

直接看代码，一切都在注释中。

```
import requests  
> from multiprocessing import Pool  
  
def parse_1():  
    url = 'https://www.baidu.com'  
    # 建池  
    > pool = Pool(processes=5)  
    # 存放结果  
    > res_lst = []  
    for i in range(300):  
        # 把任务加入池中  
        > res = pool.apply_async(func=parse_2, args=(url,))  
# 获取完成的结果(需要取出)  
        > res_lst.append(res)  
# 存放最终结果(也可以直接存储或者print)  
    > good_res_lst = []  
> forres in res_lst:  
# 利用get获取处理后的结果  
        > good_res = res.get()  
# 判断结果的好坏  
> if good_res:  
            > good_res_lst.append(good_res)  
# 关闭和等待完成  
    > pool.close()  
    > pool.join()  
  
defparse_2(url):  
    response = requests.get(url)  
    print(response.status_code)  
  
if__name__ == '__main__':  
    parse_1()
```

  

可以看到 `multiprocessing` 库的代码稍繁琐，但支持更多的拓展。**多进程和多线程确实能够达到加速的目的，但如果遇到 IO 阻塞会出现线程或者进程的浪费**，因此有一个更好的方法……

####   

五、异步非阻塞

![](https://oscimg.oschina.net/oscnet/5cf07dc92882ceddaaaae114081738834c6.png)

**协程 + 回调** 配合动态协作就可以达到异步非阻塞的目的，本质只用了一个线程，所以很大程度利用了资源  

实现异步非阻塞经典是利用 `asyncio` 库 + `yield` ，为了方便利用逐渐出现了更上层的封装 `aiohttp` ，要想更好的理解异步非阻塞最好还是深入了解 `asyncio` 库。而 `gevent` 是一个非常方便实现协程的库

```
import requests  
> from gevent import monkey  
# 猴子补丁是协作运行的灵魂  
> monkey.patch_all()  
> import gevent  
  
def parse_1():  
    url = 'https://www.baidu.com'  
    # 建立任务列表  
    > tasks_list = []  
    for i in range(300):  
        > task = gevent.spawn(parse_2, url)  
        > tasks_list.append(task)  
    > gevent.joinall(tasks_list)  
  
def parse_2(url):  
    response = requests.get(url)  
    print(response.status_code)  
  
if __name__ == '__main__':  
    parse_1()
```

gevent 能很大提速，也引入了新的问题：**如果我们不想速度太快给服务器造成太大负担怎么办？**如果是多进程多线程的建池方法，可以控制池内数量。如果用 gevent 想要控制速度也有一个不错的方法：**建立队列。** gevent 中也提供了 **Quene 类**，下面代码改动较大

```
import requests  
from gevent import monkey  
monkey.patch_all()  
import gevent  
> from gevent.queue import Queue  
  
def parse_1():  
    url = 'https://www.baidu.com'  
    tasks_list = []  
    # 实例化队列  
    > quene = Queue()  
    for i in range(300):  
        # 全部url压入队列  
        > quene.put_nowait(url)  
    # 两路队列  
    > for _ in range(2):  
        > task = gevent.spawn(parse_2)  
        > tasks_list.append(task)  
    gevent.joinall(tasks_list)  
  
# 不需要传入参数，都在队列中  
> def parse_2():  
    # 循环判断队列是否为空  
    > while not quene.empty():  
        # 弹出队列  
        > url = quene.get_nowait()  
        response = requests.get(url)  
        # 判断队列状态  
        > print(quene.qsize(), response.status_code)  
  
if __name__ == '__main__':  
    parse_1()
```

  

结束语

![](https://oscimg.oschina.net/oscnet/5cf07dc92882ceddaaaae114081738834c6.png)

以上就是几种常用的加速方法。如果对代码测试感兴趣可以利用 time 模块判断运行时间。爬虫的加速是重要技能，但适当控制速度也是爬虫工作者的良好习惯，不要给服务器太大压力，拜拜～

  

作者：陈熹

简介：一只有着码农梦想的眼科狗。更多内容欢迎关注简书：**半为花间酒，**会不定期更新一些 python、R 语言、SQL 相关及生物信息学、网络爬虫、数据分析、可视化相关的文章。

  

![](https://oscimg.oschina.net/oscnet/63f9ee178ff69a449affcb019c497d5bb9b.png)

### 

**往期内容** （👇 猛戳可查看 ）  

  

![](https://oscimg.oschina.net/oscnet/886a7933cb7062b77d859969c81ee0cff98.gif)
 **热门文章：** 

[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [情人节网站](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247483810%26idx%3D1%26sn%3Dbffbc34633b0246c2e9878e448eae461%26chksm%3De9f0fa0dde87731b8ad7e777b086ff0ea939b5921316841a50ca043724ef7314d59c10ade9e9%26scene%3D21%23wechat_redirect)[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect)[岗位对比分析](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484594%26idx%3D1%26sn%3D5f23c9f28e069b22b3f143165ebbb05e%26chksm%3De9f0ff1dde87760b5289f916fceee43bf57bee02c84173122170075230a4ad960a7114f00bca%26scene%3D21%23wechat_redirect) [➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [爬取网易云音乐](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484306%26idx%3D1%26sn%3D9dfa1b7364218e45fc3e55690998f702%26chksm%3De9f0f83dde87712b67eb1810a085fda57899f5b99baaf9f887f439a901a3f2b182f441b833da%26scene%3D21%23wechat_redirect)

[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [微博热搜分析](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247485012%26idx%3D1%26sn%3D3260f223e33c636ced2a57bbe27b4028%26chksm%3De9f0fdfbde8774ed47207652d93b4e0f6690382bbc53b50d7e6271d3b8a39d5047d15e0c0a3d%26scene%3D21%23wechat_redirect) [➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [自动追踪快递](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484370%26idx%3D1%26sn%3D3af68e5538d8a687dde72f759ca6ae93%26chksm%3De9f0f87dde87716b7e2013caf58e944cb2a3b35e1af73e0ea4488b520346be8ff24b77e4acb7%26scene%3D21%23wechat_redirect) [➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [Python 画樱花](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484284%26idx%3D1%26sn%3D7e93fda5da229b281a2337a76125755c%26chksm%3De9f0f8d3de8771c5160538060c6a05e4c75f37e902321fcc60a38bdc6a740dac154571e39db1%26scene%3D21%23wechat_redirect) 树

[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect)[Python 斗地主](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484533%26idx%3D1%26sn%3D8c264ee3b0cd9c02701bddd7ffce7a5b%26chksm%3De9f0ffdade8776ccaa0e70dbf84c10f406f211a9cf0caf141ee1839162ac9818c6440de6f3f1%26scene%3D21%23wechat_redirect)[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect)[Matplotlib 神器](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484370%26idx%3D1%26sn%3D3af68e5538d8a687dde72f759ca6ae93%26chksm%3De9f0f87dde87716b7e2013caf58e944cb2a3b35e1af73e0ea4488b520346be8ff24b77e4acb7%26scene%3D21%23wechat_redirect)[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect)[全球疫情](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484221%26idx%3D1%26sn%3D73b7cb123623b3ef889a5ec2302a3d99%26chksm%3De9f0f892de87718425632d844d315d72be11f0ee71af8de21d62a1c064b154eb65fe0c671233%26scene%3D21%23wechat_redirect)动态图

![](https://oscimg.oschina.net/oscnet/886a7933cb7062b77d859969c81ee0cff98.gif)
 **数据分析：**  

[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [统计检验](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484512%26idx%3D1%26sn%3D13d38142a30e956a2cc62a90ed817241%26chksm%3De9f0ffcfde8776d9850b00ea764593279efeb43edfdec8335f7eb2f88aa4e6aff2b3ae2d9177%26scene%3D21%23wechat_redirect) [➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484182%26idx%3D1%26sn%3D9db05ab46180ef83aea87ba1dba7c611%26chksm%3De9f0f8b9de8771af718ff03abaafc188e037c4af11e117e2cb982402fac2d66621afa5e5d11f%26scene%3D21%23wechat_redirect) [数据分析报告](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484182%26idx%3D1%26sn%3D9db05ab46180ef83aea87ba1dba7c611%26chksm%3De9f0f8b9de8771af718ff03abaafc188e037c4af11e117e2cb982402fac2d66621afa5e5d11f%26scene%3D21%23wechat_redirect) [➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [数据分析技巧](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484431%26idx%3D1%26sn%3D62fefb7bfb848fa48d9871bdac9bd440%26chksm%3De9f0ffa0de8776b66ed972587545934d8d61d9162d2e53c4887b3a19e07ba33e70c34f192114%26scene%3D21%23wechat_redirect)

➤ [数据可视化](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484131%26idx%3D1%26sn%3D9f8dd6b46d320502f86adc22a61ea0af%26chksm%3De9f0f94cde87705aab88ac7349485929278d74967f9008b00f4109bef7ff03fd975707131870%26scene%3D21%23wechat_redirect) ➤ [Pandas](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247483931%26idx%3D1%26sn%3D72c6ed29f7819698da8ecddd1dca40ac%26chksm%3De9f0f9b4de8770a2b63a9a4989a6546dbf3ab7bf47c98caee79d0fa6cb40ed026596d36f80ab%26scene%3D21%23wechat_redirect) 学习 ➤ [缺失值处理](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484170%26idx%3D1%26sn%3Daf5873bc9494535544ae224ddce93851%26chksm%3De9f0f8a5de8771b3d1973fa01fde5a129e123283e9424f6b7608bbb5a99fb3e705bb2713228f%26scene%3D21%23wechat_redirect)

[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [Python](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484003%26idx%3D1%26sn%3D2683027b5f32304c0cb9c6766c755c83%26chksm%3De9f0f9ccde8770da3e8a4bcf1309ff8d5acbdcff67f6ebdd19ecfe8e4dbdce81b5bb44d24412%26scene%3D21%23wechat_redirect) 库整理[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect)[数据降维](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484541%26idx%3D1%26sn%3Da6060384133f1b978af6e04703899dc4%26chksm%3De9f0ffd2de8776c465dfe030114600875eb6ec34ec32a8d1f5c7fdef3a057e6dc48c2d42ae78%26scene%3D21%23wechat_redirect)[➤](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect) [疫情数据汇总](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI1MTUyMjc1Mg%3D%3D%26mid%3D2247484264%26idx%3D3%26sn%3D2907754bb4168749e67959705a0cab82%26chksm%3De9f0f8c7de8771d1812ca16a201c2d70d05ecece9d034d68ba824d469cfd630ffc5b5def28fe%26scene%3D21%23wechat_redirect)

  

![](https://oscimg.oschina.net/oscnet/0e0a6bb2424b00098fab68df401f037a14a.png)
  

**记得点个** **在看** **支持下～👇**

![](https://oscimg.oschina.net/oscnet/2f76895cc365dc0a8f258d89b9826d845db.png)

本文分享自微信公众号 - 早起 Python（zaoqi-python）。  
如有侵权，请联系 support@oschina.cn 删除。  
本文参与 “[OSC 源创计划](https://www.oschina.net/sharing-plan)”，欢迎正在阅读的你也加入，一起分享。

展开阅读全文

[gevent](https://www.oschina.net/p/gevent)[python](https://www.oschina.net/p/python)[r 语言](https://www.oschina.net/p/r-language)  [matplotlib](https://www.oschina.net/p/matplotlib)

本文转载自网络

举报

加载中

![](https://static.oschina.net/new-osc/img/portrait.gif)

[点击引领话题📣](https://www.oschina.net/comment/blog/4366709)

取消

发布

### 作者的其它热门文章

[代码详解Python多线程、多进程、协程](https://my.oschina.net/u/4579171/blog/4366655 "代码详解Python多线程、多进程、协程")

[代码详解Python多线程、多进程、协程](https://my.oschina.net/u/4579171/blog/4366701 "代码详解Python多线程、多进程、协程")

[代码详解Python多线程、多进程、协程](https://my.oschina.net/u/4579171/blog/4366674 "代码详解Python多线程、多进程、协程")

[代码详解Python多线程、多进程、协程](https://my.oschina.net/u/4579171/blog/4366687 "代码详解Python多线程、多进程、协程")

[代码详解Python多线程、多进程、协程](https://my.oschina.net/u/4579171/blog/4366671 "代码详解Python多线程、多进程、协程")

打赏

0 赞

0 收藏

微信 QQ 微博

分享

### 关于作者

[

![](https://static.oschina.net/uploads/user/2289/4579171_200.jpg?t=1594100704000)


](https://my.oschina.net/u/4579171)

![](https://static.oschina.net/new-osc/img/level/lv6_small.png)

[刘早起](https://my.oschina.net/u/4579171)

关注

[私信](https://my.oschina.net/u/4579171)

[提问](https://www.oschina.net/question/ask?user=4579171)

[

文章

531

](https://my.oschina.net/u/4579171)

经验值

7.2K

[

粉丝

29

](https://my.oschina.net/u/4579171/followers)[

关注

0

](https://my.oschina.net/u/4579171/following)

#### 作者的专辑

[全部](https://my.oschina.net/u/4579171 "查看全部专辑")

[早起Python(531)](https://my.oschina.net/u/4579171?tab=newest&catalogId=7031888 "早起Python")

 [![](https://static.oschina.net/uploads/cooperation/blog_detail_right_sidebar_2_jMMoT.jpg)](https://www.oschina.net/action/visit/ad?id=1440) 

源创计划

[立即入驻](https://www.oschina.net/sharing-plan)

自媒体入驻开源社区，

获百万流量，打造个人技术品牌

### 推荐关注

换一批

[

![](https://oscimg.oschina.net/oscnet/up-863bdfafb90b0fe25faf9b18d877e32c.jpg!/both/50x50?t=1524707642000)


](https://my.oschina.net/love404 "登录-注册")

[登录-注册](https://my.oschina.net/love404 "登录-注册")

文章 36

访问 3.4K

[

![](https://static.oschina.net/uploads/user/363/726323_50.jpeg?t=1474810076000)


](https://my.oschina.net/zgldh "zgldh")

[zgldh](https://my.oschina.net/zgldh "zgldh")

文章 50

访问 35.3W

[

![](https://static.oschina.net/uploads/user/877/1755041_50.jpg?t=1449466412000)


](https://my.oschina.net/u/1755041 "小星心")

[小星心](https://my.oschina.net/u/1755041 "小星心")

开源软件作者

[

![](https://static.oschina.net/uploads/user/437/875912_50.jpg?t=1383872767000)


](https://my.oschina.net/u/875912 "沧海-ZHA")

[沧海-ZHA](https://my.oschina.net/u/875912 "沧海-ZHA")

开源软件作者

[

![](https://static.oschina.net/uploads/user/590/1181435_50.jpeg?t=1398829918000)


](https://my.oschina.net/lifephp "lifephp")

[lifephp](https://my.oschina.net/lifephp "lifephp")

文章 16

访问 4.7W

打赏

[](https://www.oschina.net/comment/blog/4366709)

0 评论

0 收藏

0 赞

微信 QQ 微博

分享

选择专区和圈子：

取消

确定

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

深圳市奥思网络科技有限公司版权所有

[粤ICP备12009483号](http://beian.miit.gov.cn/)

![](https://oscimg.oschina.net/oscnet/up-02f2706a81344119fb5cdcdda304068f2e0.png)
 ![](https://oscimg.oschina.net/oscnet/up-e77d060131d9b392981650ec7beb614554f.JPEG)

![](https://static.oschina.net/new-osc/img/icon/back-to-top.svg)

顶部