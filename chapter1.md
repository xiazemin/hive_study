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

Caused by: javax.jdo.JDODataStoreException: Required table missing : "DBS" in Catalog "" Schema "". DataNucleus requires this table to perform its persistence operations. Either your MetaData is incorrect, or you need to enable "datanucleus.schema.autoCreateTables"

NestedThrowables:

org.datanucleus.store.rdbms.exceptions.MissingTableException: Required table missing : "DBS" in Catalog "" Schema "". DataNucleus requires this table to perform its persistence operations. Either your MetaData is incorrect, or you need to enable "datanucleus.schema.autoCreateTables"

原因

datanucleus.autoCreateSchema is not a valid property in DataNucleus 4.0 \(see the properties doc\), as defined by the migration guide from v3.x. Using datanucleus.schema.autoCreateAll would make more sense.

$ vi conf/hive-site.xml

&lt;name&gt;datanucleus.schema.autoCreateAll&lt;/name&gt;

```
&lt;value&gt;true&lt;/value&gt;
```

$ hive --service metastore &

\[1\] 9852

 2017-08-11 19:55:50: Starting Hive Metastore Server

/Users/didi/hive/hive/bin/ext/metastore.sh: line 29: export: \` -Dproc\_metastore  -Dlog4j.configurationFile=hive-log4j2.properties  -Djava.util.logging.config.file=/Users/didi/hive/hive/conf/parquet-logging.properties  ': not a valid identifier

2017-08-11T19:55:54,413 INFO \[main\] org.apache.hadoop.hive.metastore.HiveMetaStore - STARTUP\_MSG:

/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

STARTUP\_MSG: Starting HiveMetaStore

STARTUP\_MSG:   host = localhost/127.0.0.1

STARTUP\_MSG:   args = \[\]

STARTUP\_MSG:   version = 2.3.0



