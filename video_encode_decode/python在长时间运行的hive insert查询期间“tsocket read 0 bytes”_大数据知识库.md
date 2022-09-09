# python在长时间运行的hive insert查询期间“tsocket read 0 bytes”_大数据知识库
python在长时间运行的hive insert查询期间“tsocket read 0 bytes”\_大数据知识库

[](https://www.saoniuhuo.com "大数据知识库")

*   [首页](/)
*   [问答库](/question/)
    
*   [知识库](/article)
    
*   [教程库](/column)
    
*   [标签](/topic)
*   [导航](/hao)
*   [书籍](/book)

[登录](/user/login)[注册](/user/register)

*   
*   [投稿](/article/collect)

python在长时间运行的hive insert查询期间“tsocket read 0 bytes”
==================================================

[oyt4ldly](/user/profile-1645.html)  于 2021-06-27  发布在  [Hive](/question/list-20/)

关注(0)|答案(1)|浏览(742)

我正在使用pyhive0.6.1在hive中运行一个长的ish insert查询，结果失败了 `thrift.transport.TTransport.TTransportException: TSocket read 0 bytes` 大约5分钟后。在服务器端，查询将一直运行，直到成功完成。我对快速查询没有这个问题。  
我不能用相同的python版本在mac上本地复制它：代码正确地等待，直到查询完成。发生这种情况的环境是基于python:3.6-slim. 除此之外，我正在安装libsasl2 dev和libsasl2 modules包，以及pyhive\[hive\]python包。  
你知道为什么会这样吗？提前谢谢。  
我使用的代码是：

```


1.  `import contextlib`
2.  `from pyhive.hive import connect`

4.  `def get_conn():`
5.   `return connect(`
6.   `host='my-host',`
7.   `port=10000,`
8.   `auth='NONE',`
9.   `username='username',`
10.   `database='database'`
11.   `)`

13.  `with contextlib.closing(get_conn())  as conn, \`
14.   `contextlib.closing(conn.cursor())  as cur:`
15.   `cur.execute('My long insert statement')`


```

这是完整的回溯

```


1.  `Traceback  (most recent call last):`
2.   `File  "<stdin>", line 5,  in  <module>`
3.   `File  "/usr/local/lib/python3.6/site-packages/pyhive/hive.py", line 364,  in execute`
4.   `response =  self._connection.client.ExecuteStatement(req)`
5.   `File  "/usr/local/lib/python3.6/site-packages/TCLIService/TCLIService.py", line 280,  in  ExecuteStatement`
6.   `return  self.recv_ExecuteStatement()`
7.   `File  "/usr/local/lib/python3.6/site-packages/TCLIService/TCLIService.py", line 292,  in recv_ExecuteStatement`
8.   `(fname, mtype, rseqid)  = iprot.readMessageBegin()`
9.   `File  "/usr/local/lib/python3.6/site-packages/thrift/protocol/TBinaryProtocol.py", line 134,  in readMessageBegin`
10.   `sz =  self.readI32()`
11.   `File  "/usr/local/lib/python3.6/site-packages/thrift/protocol/TBinaryProtocol.py", line 217,  in readI32`
12.   `buff =  self.trans.readAll(4)`
13.   `File  "/usr/local/lib/python3.6/site-packages/thrift/transport/TTransport.py", line 60,  in readAll`
14.   `chunk =  self.read(sz - have)`
15.   `File  "/usr/local/lib/python3.6/site-packages/thrift_sasl/__init__.py", line 166,  in read`
16.   `self._read_frame()`
17.   `File  "/usr/local/lib/python3.6/site-packages/thrift_sasl/__init__.py", line 170,  in _read_frame`
18.   `header =  self._trans.readAll(4)`
19.   `File  "/usr/local/lib/python3.6/site-packages/thrift/transport/TTransport.py", line 60,  in readAll`
20.   `chunk =  self.read(sz - have)`
21.   `File  "/usr/local/lib/python3.6/site-packages/thrift/transport/TSocket.py", line 132,  in read`
22.   `message='TSocket read 0 bytes')`
23.  `thrift.transport.TTransport.TTransportException:  TSocket read 0 bytes`

25.  `During handling of the above exception, another exception occurred:`

27.  `Traceback  (most recent call last):`
28.   `File  "<stdin>", line 5,  in  <module>`
29.   `File  "/usr/local/lib/python3.6/contextlib.py", line 185,  in __exit__`
30.   `self.thing.close()`
31.   `File  "/usr/local/lib/python3.6/site-packages/pyhive/hive.py", line 221,  in close`
32.   `response =  self._client.CloseSession(req)`
33.   `File  "/usr/local/lib/python3.6/site-packages/TCLIService/TCLIService.py", line 218,  in  CloseSession`
34.   `return  self.recv_CloseSession()`
35.   `File  "/usr/local/lib/python3.6/site-packages/TCLIService/TCLIService.py", line 230,  in recv_CloseSession`
36.   `(fname, mtype, rseqid)  = iprot.readMessageBegin()`
37.   `File  "/usr/local/lib/python3.6/site-packages/thrift/protocol/TBinaryProtocol.py", line 134,  in readMessageBegin`
38.   `sz =  self.readI32()`
39.   `File  "/usr/local/lib/python3.6/site-packages/thrift/protocol/TBinaryProtocol.py", line 217,  in readI32`
40.   `buff =  self.trans.readAll(4)`
41.   `File  "/usr/local/lib/python3.6/site-packages/thrift/transport/TTransport.py", line 60,  in readAll`
42.   `chunk =  self.read(sz - have)`
43.   `File  "/usr/local/lib/python3.6/site-packages/thrift_sasl/__init__.py", line 166,  in read`
44.   `self._read_frame()`
45.   `File  "/usr/local/lib/python3.6/site-packages/thrift_sasl/__init__.py", line 170,  in _read_frame`
46.   `header =  self._trans.readAll(4)`
47.   `File  "/usr/local/lib/python3.6/site-packages/thrift/transport/TTransport.py", line 60,  in readAll`
48.   `chunk =  self.read(sz - have)`
49.   `File  "/usr/local/lib/python3.6/site-packages/thrift/transport/TSocket.py", line 132,  in read`
50.   `message='TSocket read 0 bytes')`
51.  `thrift.transport.TTransport.TTransportException:  TSocket read 0 bytes`


```

[Hive](/topic/2785/question)[python](/topic/2860/question)[thrift](/topic/3543/question)[pyhive](/topic/4739/question)

来源：[https://stackoverflow.com/questions/52668347/tsocket-read-0-bytes-during-a-long-running-hive-insert-query](/link?url=https://stackoverflow.com/questions/52668347/tsocket-read-0-bytes-during-a-long-running-hive-insert-query)

*   [关注](javascript:void(0);)
*   [举报](javascript:void(0);)

1条答案
====

[按热度](/question/detail-2054268.html?sort=hot)[按时间](/question/detail-2054268.html?sort=new)

[![](https://www.saoniuhuo.com/home/images/avatar/default_avator.png)
](/user/profile-73.html)

[gopyfrb3](/user/profile-73.html)1#

引发的代码异常如下：

```


1.  `def read(self, sz):`
2.   `try:`
3.   `buff =  self.handle.recv(sz)`
4.   `except socket.error as e:`
5.   `if  (e.args[0]  == errno.ECONNRESET and`
6.   `(sys.platform ==  'darwin'  or sys.platform.startswith('freebsd'))):`
7.   `# freebsd and Mach don't follow POSIX semantic of recv`
8.   `# and fail with ECONNRESET if peer performed shutdown.`
9.   `# See corresponding comment and code in TSocket::read()`
10.   `# in lib/cpp/src/transport/TSocket.cpp.`
11.   `self.close()`
12.   `# Trigger the check to raise the END_OF_FILE exception below.`
13.   `buff =  ''`
14.   `else:`
15.   `raise`
16.   `if len(buff)  ==  0:`
17.   `raise  TTransportException(type=TTransportException.END_OF_FILE,`
18.   `message='TSocket read 0 bytes')`
19.   `return buff`


```

我想这可能是会议提出的 `errno.ECONNRESET` 服务器故意关闭连接时可能发生的错误(根据这个节点js econnreset，服务器可能会在太忙时终止连接，并发现连接已超过“keep alive”超时） 您可以检查服务器的日志，并找出是否存在某种终止连接行为。 我不确定，只是提供了我的想法。

展开查看全部

[赞(0）](javascript:void(0);)[分享  ](javascript:void(0);)[回复(0）](javascript:void(0);)[举报  ](javascript:void(0);)2021-06-27

*   [首页](/question/detail-2054268.html?sort=hot&page=1)
*   [上一页](javascript:void(0))
*   [1](javascript:void(0))
*   [下一页](javascript:void(0))
*   [末页](/question/detail-2054268.html?sort=hot&page=1)

[我来回答](javascript:void(0);)

相关问题
====

*   2回答
    
    706浏览
    
    [tsocketread 0 bytes（code-thrifttransport）：tttransportexception（'tsocketread 0 bytes'，）](/question/detail-2046890.html) [Hive](/topic/2785/question)[hue](/topic/2889/question)
    
    [Hive](/question/list-20/) [hc2pp10m](/user/profile-1118.html)2021-06-25预览 (706)2021-06-25 
    
*   3回答
    
    218浏览
    
    [hive：优化长时间运行的查询](/question/detail-1952364.html)[sql](/topic/2769/question)[hadoop](/topic/2773/question)[Hive](/topic/2785/question)[apache-tez](/topic/3437/question)
    
    [Hadoop](/question/list-16/) [mlmc2os5](/user/profile-1039.html)2021-06-03预览 (218)2021-06-03 
    
*   1回答
    
    169浏览
    
    [长时间运行的查询sql](/question/detail-2103259.html) [sql](/topic/2769/question)[sql-server](/topic/2974/question)[performance](/topic/2986/question)
    
    [Java](/question/list-14/) [nr9pn0ug](/user/profile-1636.html)2021-07-26预览 (169)2021-07-26 
    
*   1回答
    
    238浏览
    
    [为什么happybase在运行table.scan（）时返回“tsocketread 0 bytes”？](/question/detail-1980040.html) [python](/topic/2860/question)[hbase](/topic/2786/question)[thrift](/topic/3543/question)[happybase](/topic/4602/question)
    
    [Hbase](/question/list-22/) [qnakjoqk](/user/profile-1556.html)2021-06-09预览 (238)2021-06-09 
    
*   0回答
    
    107浏览
    
    [ApacheKafka—使用java编程实现具有巨大结果集的长时间运行查询](/question/detail-1967321.html)[Java](/topic/2764/question)[apache-kafka](/topic/2880/question)
    
    [Kafka](/question/list-27/) [euoag5mw](/user/profile-832.html)2021-06-06预览 (107)2021-06-06 
    
*   0回答
    
    167浏览
    
    [spark长时间运行操作](/question/detail-1920859.html) [scala](/topic/2818/question)[apache-spark](/topic/2937/question)[nearest-neighbor](/topic/4667/question)
    
    [Spark](/question/list-29/) [bqujaahr](/user/profile-127.html)2021-05-29预览 (167)2021-05-29 
    
*   1回答
    
    187浏览
    
    [hbase completebulkload长时间运行](/question/detail-1922232.html)[hadoop](/topic/2773/question)[hbase](/topic/2786/question)[bulk-load](/topic/3774/question)
    
    [Hadoop](/question/list-16/) [klh5stk1](/user/profile-262.html)2021-05-29预览 (187)2021-05-29 
    
*   1回答
    
    169浏览
    
    [hadoop jobtracker如何处理长时间运行的任务](/question/detail-1952771.html) [hadoop](/topic/2773/question)
    
    [Hadoop](/question/list-16/) [jslywgbw](/user/profile-1152.html)2021-06-03预览 (169)2021-06-03 
    
*   2回答
    
    191浏览
    
    [mysql-没有正确索引的长时间运行查询](/question/detail-2025804.html)[mysql](/topic/2775/question)[performance](/topic/2986/question)[optimization](/topic/2987/question)[indexing](/topic/3186/question)[query-optimization](/topic/3140/question)
    
    [Mysql](/question/list-74/) [wf82jlnq](/user/profile-694.html)2021-06-21预览 (191)2021-06-21 
    
*   0回答
    
    257浏览
    
    [thrift hbase python\->thrift.transport.tttransport.tttransportexception:tsocketread 0 bytes](/question/detail-1920009.html)[python](/topic/2860/question)[hadoop](/topic/2773/question)[hbase](/topic/2786/question)[thrift](/topic/3543/question)[happybase](/topic/4602/question)
    
    [Hadoop](/question/list-16/) [gr8qqesn](/user/profile-1192.html)2021-05-27预览 (257)2021-05-27 
    
*   0回答
    
    215浏览
    
    [Spark与数据集长时间运行的工作](/question/detail-1913930.html) [apache-spark](/topic/2937/question)[yarn](/topic/2811/question)
    
    [Spark](/question/list-29/) [hgncfbus](/user/profile-581.html)2021-05-24预览 (215)2021-05-24 
    
*   0回答
    
    186浏览
    
    [hadoop：诊断长时间运行的作业](/question/detail-1920444.html) [hadoop](/topic/2773/question)[Hive](/topic/2785/question)[mapreduce](/topic/2805/question)
    
    [Hadoop](/question/list-16/) [wkyowqbh](/user/profile-1627.html)2021-05-27预览 (186)2021-05-27 
    
*   0回答
    
    188浏览
    
    [长时间运行应用程序的kerberos问题](/question/detail-1922911.html) [hadoop](/topic/2773/question)[yarn](/topic/2811/question)[hadoop2](/topic/3425/question)
    
    [Hadoop](/question/list-16/) [b91juud3](/user/profile-1672.html)2021-05-29预览 (188)2021-05-29 
    
*   1回答
    
    194浏览
    
    [配置单元脚本正在长时间运行](/question/detail-1933162.html)[hadoop](/topic/2773/question)[amazon-web-services](/topic/3171/question)[Hive](/topic/2785/question)[emr](/topic/4387/question)
    
    [Hadoop](/question/list-16/) [zynd9foi](/user/profile-246.html)2021-05-30预览 (194)2021-05-30 
    
*   1回答
    
    180浏览
    
    [在mysql中杀死长时间运行的进程](/question/detail-2042408.html) [mysql](/topic/2775/question)[mariadb](/topic/3060/question)[query-optimization](/topic/3140/question)[Kill](/topic/10245/question)[mysql-slow-query-log](/topic/8943/question)
    
    [Mysql](/question/list-74/) [hgc7kmma](/user/profile-903.html)2021-06-25预览 (180)2021-06-25 
    

[查看更多](/search/question?keyword=python在长时间运行的hive insert查询期间“tsocket read 0 bytes”)

热门标签
====

[更多](/topic/)

[Java](/topic/2764)[query](/topic/18663)[Node](/topic/17205)[python](/topic/2860)[request](/topic/7522)[开发语言](/topic/17430)[Util](/topic/42308)[Table](/topic/40343)[Logger](/topic/21456)[后端](/topic/16473)[Message](/topic/6942)[Element](/topic/3906)[Parser](/topic/36893)[response](/topic/6401)[Utils](/topic/42352)

热门问题
====

[更多](/question/)

*   [查询 clickhouse 当前安装的版本](/question/detail-1911180.html)
    
    回答(2) 发布于 2021-01-14
    
*   [springboot应用程序启动失败parameter 1 of constructor in that could not be found](/question/detail-1911564.html)
    
    回答(3) 发布于 2021-01-30
    
*   [日期验证](/question/detail-2000927.html)
    
    回答(2) 发布于 2021-06-18
    
*   [clickhouse 查询使用正则表达式](/question/detail-1911163.html)
    
    回答(1) 发布于 2021-01-14
    
*   [ClickHouse通过jdbc查询数据时偶尔会遇到这个错误ru.yandex.clickhouse.except.ClickHouseUnknownException: ClickHouse exception](/question/detail-1910990.html)
    
    回答(1) 发布于 2021-01-11
    
*   [asp.net:javascript函数在从button click事件调用时工作，而不是从redis的subscription事件调用时工作](/question/detail-1980545.html)
    
    回答(1) 发布于 2021-06-09
    

*   [技术知识](/article)
*   [关于我们](/html/aboutus.html)
*   [联系我们](/html/contactus.html)
*   [免责声明](/html/statement.html)

*   [蜀ICP备13028337号-1](http://www.beian.miit.gov.cn/) 大数据知识库 https://www.saoniuhuo.com © All rights reserved
*   本站内容来源互联网,如果侵犯您的权益请联系我们删除, 联系方式：448109455@qq.com