# ide连接

我们使用Eclipse作为开发IDE，在Eclipse中创建hive工程，并导入Hive JDBC远程连接相关包，所需的包如下所示：

hive-jdbc-0.13.1.jar

commons-logging-1.1.3.jar

hive-exec-0.13.1.jar

hive-metastore-0.13.1.jar

hive-service-0.13.1.jar

libfb303-0.9.0.jar

slf4j-api-1.6.1.jar

hadoop-common-2.2.0.jar

log4j-1.2.16.jar

slf4j-nop-1.6.1.jar

httpclient-4.2.5.jar

httpcore-4.2.5.jar

不包含hadoop-common-2.2.0.jar  会报异常

Exception in thread "main" java.sql.SQLException: Error while processing statement: FAILED: Execution Error, return code 1 from org.apache.hadoop.hive.ql.exec.DDLTask. MetaException\(message:Got exception: org.apache.hadoop.security.AccessControlException Permission denied: user=APP, access=WRITE, inode="/user/hive/warehouse":didi:supergroup:drwxr-xr-xat org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.checkFsPermission\\(FSPermissionChecker.java:271\\)

$ hdfs dfs -chmod 777  /user/hive/warehouse

SLF4J: See [http://www.slf4j.org/codes.html\#StaticLoggerBinder](http://www.slf4j.org/codes.html#StaticLoggerBinder) for further details.

Create table success!

Running: show tables 'userdb'

userdb

Running: describe userdb

key    int

value    string

Running: select count\(1\) from userdb

0

0: jdbc:hive2://localhost:10000/&gt; show tables;

+-----------+--+

\| tab\_name  \|

+-----------+--+

\| userdb    \|

+-----------+--+

1 row selected \(0.155 seconds\)

0: jdbc:hive2://localhost:10000/&gt; select \* from userdb ;

+-------------+---------------+--+

\| userdb.key  \| userdb.value  \|

+-------------+---------------+--+

+-------------+---------------+--+

No rows selected \(0.124 seconds\)

