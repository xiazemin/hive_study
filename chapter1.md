# 问题

FAILED: SemanticException org.apache.hadoop.hive.ql.metadata.HiveException: java.lang.RuntimeException: Unable to instantiate org.apache.hadoop.hive.ql.metadata.SessionHiveMetaStoreClient

原因：因为没有正常启动Hive 的 Metastore Server服务进程。

解决方法：启动Hive 的 Metastore Server服务进程，执行如下命令：

$hive --service metastore &



