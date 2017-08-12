# 插入数据



0: jdbc:hive2://localhost:10000/&gt; insert into userdb values \(1234,'hello','rd','2017-08-12','test'\);

INFO  : Number of reduce tasks is set to 0 since there's no reduce operator

INFO  : number of splits:1

INFO  : Submitting tokens for job: job\_local488803043\_0006

INFO  : The url to track the job: http://localhost:8080/

INFO  : Job running in-process \(local Hadoop\)

INFO  : 2017-08-12 21:41:22,219 Stage-1 map = 100%,  reduce = 0%

INFO  : Ended Job = job\_local488803043\_0006

INFO  : Stage-4 is selected by condition resolver.

INFO  : Stage-3 is filtered out by condition resolver.

INFO  : Stage-5 is filtered out by condition resolver.

INFO  : Moving data to: hdfs://localhost:8020/user/hive/warehouse/userdb/.hive-staging\_hive\_2017-08-12\_21-41-20\_867\_9222900556051858753-2/-ext-10000 from hdfs://localhost:8020/user/hive/warehouse/userdb/.hive-staging\_hive\_2017-08-12\_21-41-20\_867\_9222900556051858753-2/-ext-10002

INFO  : Loading data to table default.userdb from hdfs://localhost:8020/user/hive/warehouse/userdb/.hive-staging\_hive\_2017-08-12\_21-41-20\_867\_9222900556051858753-2/-ext-10000

INFO  : Table default.userdb stats: \[numFiles=5, numRows=2, totalSize=84, rawDataSize=49\]

No rows affected \(1.54 seconds\)

0: jdbc:hive2://localhost:10000/&gt; select \* from userdb;

+-------------+---------------+--------------+------------------+--------------+--+

\| userdb.key  \| userdb.value  \| userdb.dept  \| userdb.birthday  \| userdb.name  \|

+-------------+---------------+--------------+------------------+--------------+--+

\| 1213        \| hello         \| NULL         \| NULL             \| NULL         \|

\| 1214        \| hello         \| NULL         \| NULL             \| NULL         \|

\| 1215        \| world         \| NULL         \| NULL             \| NULL         \|

\| 123         \| hello         \| rd           \| NULL             \| test         \|

\| 1234        \| hello         \| rd           \| 2017-08-12       \| test         \|

+-------------+---------------+--------------+------------------+--------------+--+

5 rows selected \(0.094 seconds\)





