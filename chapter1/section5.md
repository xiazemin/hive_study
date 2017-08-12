# jdbc

Java.lang.ClassNotFoundException: org.apache.Hadoop.hive.jdbc.HiveDriver

解决方案：

Class.forName\("org.apache.hive.jdbc.HiveDriver"\);

而不是：

Class.forName\("org.apache.hadoop.hive.jdbc.HiveDriver"\);

引入hive／lib下的jar包

Exception in thread "main" java.sql.SQLException: No suitable driver found for jdbc:hive://localhost:10002/default

```
at java.sql.DriverManager.getConnection\(DriverManager.java:689\)

at java.sql.DriverManager.getConnection\(DriverManager.java:247\)

at jdbc.main\(jdbc.java:33\)
```

在 hive 1.2.1 需要 jdbc:hive2://localhost:10000/default 而不是 jdbc:hive://localhost:10000/default

log4j:WARN No appenders could be found for logger \(org.apache.hive.jdbc.Utils\).

log4j:WARN Please initialize the log4j system properly.

log4j:WARN See [http://logging.apache.org/log4j/1.2/faq.html\#noconfig](http://logging.apache.org/log4j/1.2/faq.html#noconfig) for more info.

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/hadoop/conf/Configuration

```
at org.apache.hive.jdbc.HiveConnection.createBinaryTransport\(HiveConnection.java:469\)
```

$ ./bin/hive --service hiveserver -p 10002

ls: /Users/didi/spark/spark/lib/spark-assembly-\*.jar: No such file or directory

Starting Hive Thrift Server

Exception in thread "main" java.lang.ClassNotFoundException: org.apache.hadoop.hive.service.HiveServer

$ vi etc/hadoop/hadoop-env.sh

export HADOOP\_CLASSPATH=$HADOOP\_CLASSPATH:/Users/didi/hive/hive/lib/hive-\*.jar

$ ./bin/hive --service hiveserver2 -p 10002

ls: /Users/didi/spark/spark/lib/spark-assembly-\*.jar: No such file or directory

Error starting HiveServer2 with given arguments:

Unrecognized option: -p

$ ./bin/hive --service hiveserver2 

ls: /Users/didi/spark/spark/lib/spark-assembly-\*.jar: No such file or directory

17/08/12 12:34:21 WARN conf.HiveConf: HiveConf of name hive.metastore.local does not exist

启动成功



