# server2无法连接

&lt;property&gt;

&lt;name&gt;hive.server2.thrift.port&lt;/name&gt;

&lt;value&gt;10000&lt;/value&gt;

&lt;/property&gt;

&lt;property&gt;

&lt;name&gt;hive.server2.thrift.bind.host&lt;/name&gt;

&lt;value&gt;localhost&lt;/value&gt; &lt;!-- 默认是localhost，但我手动改成了本机的ip地址,很可能就是我改了这个才起作用的 --&gt;

&lt;/property&gt;

$ vi ./conf/hive-site.xml

&lt;property&gt;

```
&lt;name&gt;hive.log4j.file&lt;/name&gt;

&lt;value&gt;/Users/didi/hive/hive/iotmp/&lt;/value&gt;
```

&lt;/property&gt;

$ cp hive-log4j.properties.template hive-log4j.properties

$ vi hive-log4j.properties

\#hive.log.dir=${java.io.tmpdir}/${user.name}

hive.log.dir=/Users/didi/hive/hive/iotmp

hive.log.file=hive.log

```
at org.apache.derby.impl.sql.conn.GenericLanguageConnectionContext.prepareInternalStatement\(Unknown Source\)
```

HiveServer2提供了一个新的命令行工具Beeline，它是基于SQLLine CLI的JDBC客户端。关于SQLLine的的知识，可以参考这个网站：http://sqlline.sourceforge.NET/\#manual

Beeline工作模式有两种，即本地嵌入模式和远程模式。嵌入模式情况下，它返回一个嵌入式的Hive（类似于hive CLI）。而远程模式则是通过Thrift协议与某个单独的HiveServer2进程进行连接通信。

