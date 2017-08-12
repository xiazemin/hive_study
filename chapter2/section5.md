# 操作



0: jdbc:hive2://localhost:10000/&gt; insert into userdb \(key,value\) values \(1215,"world"\);

INFO  : Number of reduce tasks is set to 0 since there's no reduce operator

INFO  : number of splits:1

INFO  : Submitting tokens for job: job\_local303009228\_0004

INFO  : The url to track the job: http://localhost:8080/

INFO  : Job running in-process \(local Hadoop\)

INFO  : 2017-08-12 19:09:30,649 Stage-1 map = 100%,  reduce = 0%

INFO  : Ended Job = job\_local303009228\_0004

INFO  : Stage-4 is selected by condition resolver.

INFO  : Stage-3 is filtered out by condition resolver.

INFO  : Stage-5 is filtered out by condition resolver.

INFO  : Moving data to: hdfs://localhost:8020/user/hive/warehouse/userdb/.hive-staging\_hive\_2017-08-12\_19-09-29\_319\_1340244173633736320-2/-ext-10000 from hdfs://localhost:8020/user/hive/warehouse/userdb/.hive-staging\_hive\_2017-08-12\_19-09-29\_319\_1340244173633736320-2/-ext-10002

INFO  : Loading data to table default.userdb from hdfs://localhost:8020/user/hive/warehouse/userdb/.hive-staging\_hive\_2017-08-12\_19-09-29\_319\_1340244173633736320-2/-ext-10000

INFO  : Table default.userdb stats: \[numFiles=3, numRows=3, totalSize=33, rawDataSize=30\]

No rows affected \(1.482 seconds\)



