# 问题

FAILED: SemanticException org.apache.hadoop.hive.ql.metadata.HiveException: java.lang.RuntimeException: Unable to instantiate org.apache.hadoop.hive.ql.metadata.SessionHiveMetaStoreClient

原因：因为没有正常启动Hive 的 Metastore Server服务进程。

解决方法：启动Hive 的 Metastore Server服务进程，执行如下命令：

$ hive --service metastore &

\[1\] 9556

localhost:hive didi$ 2017-08-11 19:38:14: Starting Hive Metastore Server

/Users/didi/hive/hive/bin/ext/metastore.sh: line 29: export: \` -Dproc\_metastore  -Dlog4j.configurationFile=hive-log4j2.properties  -Djava.util.logging.config.file=/Users/didi/hive/hive/conf/parquet-logging.properties  ': not a valid identifier

SLF4J: Class path contains multiple SLF4J bindings.

2017-08-11T19:38:21,200 ERROR \[main\] org.apache.hadoop.hive.metastore.HiveMetaStore - MetaException\(message:Version information not found in metastore. \)2017-08-11T19:38:21,203 INFO \[Thread-1\] org.apache.hadoop.hive.metastore.HiveMetaStore - Shutting down hive metastore.

2017-08-11T19:38:21,630 INFO \[Thread-1\] org.apache.hadoop.hive.metastore.HiveMetaStore - SHUTDOWN\_MSG:

/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

SHUTDOWN\_MSG: Shutting down HiveMetaStore at localhost/127.0.0.1

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

\[1\]+  Exit 1                  hive --service metastore

修改conf/hive-site.xml 中的 “hive.metastore.schema.verification”  值为 false  即可解决 “Caused by: MetaException\(message:Version information not found in metastore. \)” 

