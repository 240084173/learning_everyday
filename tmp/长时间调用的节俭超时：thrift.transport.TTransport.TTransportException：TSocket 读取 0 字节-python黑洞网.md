# 长时间调用的节俭超时：thrift.transport.TTransport.TTransportException：TSocket 读取 0 字节-python黑洞网
            长时间调用的节俭超时：thrift.transport.TTransport.TTransportException：TSocket 读取 0 字节-python黑洞网 

长时间调用的节俭超时：thrift.transport.TTransport.TTransportException：TSocket 读取 0 字节
--------------------------------------------------------------------------

发布于2021-12-02 11:00     阅读(983)     评论(0)     点赞(29)     收藏(3)

* * *

我已经使用 thrift 构建了一些 rpc 服务。每次调用可能会运行很长时间（几分钟到几小时）。我已将节俭超时设置为 2 天。

```null
transport = TSocket.TSocket(self.__host, self.__port)
transport.setTimeout(2 * 24 * 60 * 60 * 1000)

```

但是 thrift 总是在大约 600 秒后关闭连接，以下情况除外：

```null
thrift.transport.TTransport.TTransportException: TSocket read 0 bytes

```

我应该设置任何其他超时吗？（python，thrift 服务器：windows；客户端：ubuntu）

  

解决方案
----

* * *

正在断开 Thrift Transport 连接。这可能是由于网络问题或远程服务重启或超时问题。无论何时在断开连接后进行任何调用，都会导致 TTransportException。这个问题可以通过重新连接远程服务来解决。尝试使用它，在进行远程服务调用之前调用它。

```null
def repoen_transport():
    try:
        if not transport.isOpen():
            transport.open()
    except Exception, msg:
        print >> sys.stderr.write("Error reopening transport {}".format(msg))

```

