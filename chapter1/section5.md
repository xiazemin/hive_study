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

$ ./bin/hive --service hiveserver -p 10002

ls: /Users/didi/spark/spark/lib/spark-assembly-\*.jar: No such file or directory

Starting Hive Thrift Server

Exception in thread "main" java.lang.ClassNotFoundException: org.apache.hadoop.hive.service.HiveServer

$ vi etc/hadoop/hadoop-env.sh

export HADOOP\_CLASSPATH=$HADOOP\_CLASSPATH:/Users/didi/hive/hive/lib/hive-\*.jar

