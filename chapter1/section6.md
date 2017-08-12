# Hive的几种内置服务

1、cli：是Command Line Interface 的缩写，是hive的命令行界面，用的比较多，是默认服务，直接可以在命令行里使用

```
      2、hiveserver：这个可以让Hive以提供Thrift服务的服务器形式来运行，可以允许许多个不同语言编写的客户端进行通信，使用需要启动HiveServer服务以和客户端联系，我们可以通过设置HIVE\_PORT环境变量来设置服务器所监听的端口，在默认情况下，端口号为10000，这个可以通过以下方式来启动Hiverserver：

      bin/hive --service hiveserver -p 10002

      其中-p参数也是用来指定监听端口的

      3、hwi：其实就是hive web interface的缩写它是hive的web借口，是hive cli的一个web替代方案

      4、jar：与Hadoop jar等价的Hive接口，这是运行类路径中同时包含Hadoop 和Hive类的Java应用程序的简便方式

      5、metastore：在默认的情况下，metastore和hive服务运行在同一个进程中，使用这个服务，可以让metastore作为一个单独的进程运行，我们可以通过METASTOE——PORT来指定监听的端口号
```

二：Hive的三种启动方式

```
  1， hive  命令行模式

    进入hive安装目录，输入bin/hive的执行程序，或者输入 hive –service cli

    用于Linux平台命令行查询，查询语句基本跟MySQL查询语句类似

   2， hive  web界面的启动方式

    bin/hive –service hwi  （& 表示后台运行）

    用于通过浏览器来访问hive，感觉没多大用途，浏览器访问地址是：127.0.0.1:9999/hwi

   3， hive  远程服务 \(端口号10000\) 启动方式

    bin/hive –service hiveserver2  &（&表示后台运行）

    用Java，Python等程序实现通过jdbc等驱动的访问hive就用这种起动方式了，这个是程序员最需要的方式了
```

三：hiveServer/HiveServer2

```
   1：简单介绍     

    两者都允许远程客户端使用多种编程语言，通过HiveServer或者HiveServer2，客户端可以在不启动CLI的情况下对Hive中的数据进行操作，连这个和都允许远程客户端使用多种编程语言如java，Python等向hive提交请求，取回结果（从hive0.15起就不再支持hiveserver了），但是在这里我们还是要说一下hiveserver

   HiveServer或者HiveServer2都是基于Thrift的，但HiveSever有时被称为Thrift server，而HiveServer2却不会。既然已经存在HiveServer，为什么还需要HiveServer2呢？这是因为HiveServer不能处理多于一个客户端的并发请求，这是由于HiveServer使用的Thrift接口所导致的限制，不能通过修改HiveServer的代码修正。因此在Hive-0.11.0版本中重写了HiveServer代码得到了HiveServer2，进而解决了该问题。HiveServer2支持多客户端的并发和认证，为开放API客户端如JDBC、ODBC提供更好的支持。

   2：两者的区别

   Hiveserver1 和hiveserver2的JDBC区别： 

   HiveServer version               Connection URL                    Driver Class 



   HiveServer2                          jdbc:hive2://:                          org.apache.hive.jdbc.HiveDriver

   HiveServer1                          jdbc:hive://:                            org.apache.hadoop.hive.jdbc.HiveDriver



   3：学习HiveServer和HiveServer2

   HiveServer：

   在命令行输入hive --service hiveserver –help查看hiveserver的帮助信息：
```

\[html\] view plain copy  在CODE上查看代码片派生到我的代码片

\[hadoop@hadoop~\]$ hive --service hiveserver --help

Starting Hive Thrift Server

usage:hiveserver

-h,--help                        Print help information

```
--hiveconf &lt;propertyproperty=value&gt;   Use value for given property  

--maxWorkerThreads &lt;arg&gt;      maximum number of worker threads,  

                             default:2147483647  

--minWorkerThreads &lt;arg&gt;      minimum number of worker threads,  

                              default:100
```

-p &lt;port&gt;                        Hive Server portnumber, default:10000

-v,--verbose                     Verbose mode

```
   启动hiveserver服务，可以得知默认hiveserver运行在端口10000，最小100工作线程，最大2147483647工作线程。
```

\[html\] view plain copy  在CODE上查看代码片派生到我的代码片

\[hadoop@hadoop~\]$ hive --service hiveserver -v

Starting Hive Thrift Server

14/08/01 11:07:09WARN conf.HiveConf: DEPRECATED: hive.metastore.ds.retry.\* no longer has anyeffect.  Use hive.hmshandler.retry.\*instead

Starting hive serveron port 10000 with 100 min worker threads and 2147483647 maxworker threads

```
   以上的hiveserver在hive1.2.1中并不会出现，官网的说法是：

   HiveServer is scheduled to be removed from Hive releases starting Hive 0.15. See HIVE-6977. Please switch over to HiveServer2.

   Hiveserver2

   Hiveserver2允许在配置文件hive-site.xml中进行配置管理，具体的参数为：
```

\[html\] view plain copy  在CODE上查看代码片派生到我的代码片

hive.server2.thrift.min.worker.threads– 最小工作线程数，默认为5。

hive.server2.thrift.max.worker.threads – 最小工作线程数，默认为500。

hive.server2.thrift.port– TCP 的监听端口，默认为10000。

hive.server2.thrift.bind.host– TCP绑定的主机，默认为localhost

```
   也可以设置环境变量HIVE\_SERVER2\_THRIFT\_BIND\_HOST和HIVE\_SERVER2\_THRIFT\_PORT覆盖hive-site.xml设置的主机和端口号。从Hive-0.13.0开始，HiveServer2支持通过HTTP传输消息，该特性当客户端和服务器之间存在代理中介时特别有用。与HTTP传输相关的参数如下：
```

\[html\] view plain copy  在CODE上查看代码片派生到我的代码片

hive.server2.transport.mode – 默认值为binary（TCP），可选值HTTP。

hive.server2.thrift.http.port– HTTP的监听端口，默认值为10001。

hive.server2.thrift.http.path – 服务的端点名称，默认为 cliservice。

hive.server2.thrift.http.min.worker.threads– 服务池中的最小工作线程，默认为5。

hive.server2.thrift.http.max.worker.threads– 服务池中的最小工作线程，默认为500。

```
    启动Hiveserver2有两种方式，一种是上面已经介绍过的hive --service hiveserver2，另一种更为简洁，为hiveserver2。使用hive--service hiveserver2 –H或hive--service hiveserver2 –help查看帮助信息：
```

\[html\] view plain copy  在CODE上查看代码片派生到我的代码片

Starting HiveServer2

Unrecognizedoption: -h

usage:hiveserver2

-H,--help                        Print help information

```
--hiveconf &lt;propertyproperty=value&gt;   Use value for given property  

   默认情况下，HiveServer2以提交查询的用户执行查询（true），如果hive.server2.enable.doAs设置为false，查询将以运行hiveserver2进程的用户运行。为了防止非加密模式下的内存泄露，可以通过设置下面的参数为true禁用文件系统的缓存：
```

\[html\] view plain copy  在CODE上查看代码片派生到我的代码片

fs.hdfs.impl.disable.cache – 禁用HDFS文件系统缓存，默认值为false。

fs.file.impl.disable.cache – 禁用本地文件系统缓存，默认值为false。

```
  4：配置使用hiveserver2（Hive 2.0为例）

    sudo vim hive-site.xml

   1\)：配置监听端口和路径
```

2\)：设置impersonation

```
  这样hive server会以提交用户的身份去执行语句，如果设置为false，则会以起hive server daemon的admin user来执行语句
```

3\):hiveserver2节点配置

Hiveserver2已经不再需要hive.metastore.local这个配置项了（hive.metastore.uris为空，则表示是metastore在本地，否则

就是远程）远程的话直接配置hive.metastore.uris即可

启动服务：

```
   1\)：启动metastore

   bin/hive --service metastore &

   默认端口为9083

   2\)：启动hiveserver2

   bin/hive --service hiveserver2 &

   3\)：测试

   Web UI：http://192.168.48.130:10002/
```



