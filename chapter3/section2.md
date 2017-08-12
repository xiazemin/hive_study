# 分区实践

建表的时候必须有分区字段定义才能加分区，否则会报

Error: Error while compiling statement: FAILED: ValidationFailureSemanticException table is not partitioned but partition spec exists: {day=12} \(state=42000,code=40000\)

0: jdbc:hive2://localhost:10000/&gt; CREATE EXTERNAL TABLE stock\_ticker \(name string\) PARTITIONED BY \(stock\_symbol STRING\);

No rows affected \(0.084 seconds\)

0: jdbc:hive2://localhost:10000/&gt; alter table stock\_ticker add if not exists partition\(stock\_symbol='ASP'\) location '/stock\_ticker/ASP'；

Error: Error while processing statement: FAILED: Execution Error, return code 1 from org.apache.hadoop.hive.ql.exec.DDLTask. MetaException\(message:Got exception: org.apache.hadoop.security.AccessControlException Permission denied: user=hive.server2.proxy.user=APP, access=WRITE, inode="/":didi:supergroup:drwxr-xr-x

$ hdfs dfs -mkdir /stock\_ticker

$ hdfs dfs -chmod 777 /stock\_ticker

0: jdbc:hive2://localhost:10000/&gt; alter table stock\_ticker add if not exists partition \( stock\_symbol='ASP' \) location '/stock\_ticker/ASP';

No rows affected \(0.107 seconds\)

0: jdbc:hive2://localhost:10000/&gt; show partitions stock\_ticker;

+-------------------+--+

\|     partition     \|

+-------------------+--+

\| stock\_symbol=ASP  \|

+-------------------+--+

1 row selected \(0.104 seconds\)



