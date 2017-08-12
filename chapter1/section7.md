# beeline

$ beeline

Beeline version 1.2.1.spark2 by Apache Hive

beeline&gt;

$ vi conf/hive-site.xml

&lt;property&gt;

&lt;name&gt;hive.server2.thrift.port&lt;/name&gt;

&lt;value&gt;10000&lt;/value&gt;

&lt;description&gt;TCP port number to listen on, default 10000&lt;/description&gt;

&lt;/property&gt;

可以通过命令启动：

     hive --service hiveserver2 --hiveconf hive.server2.thrift.port=11111   设置端口号，默认端口号为10000

     也可以通过hiveserver2 直接启动，这时端口号为默认10000

$  ./bin/hive --service hiveserver2

$  ./bin/hive --service hiveserver2 --hiveconf hive.server2.thrift.port=10001

&gt;  !connect jdbc:hive2://localhost:10001  org.apache.hive.jdbc.HiveDriver

17/08/12 14:40:52 INFO jdbc.HiveConnection: Could not open client transport with JDBC Uri: jdbc:hive2://localhost:10000

17/08/12 14:40:52 INFO jdbc.HiveConnection: Transport Used for JDBC connection: null

Error: Could not open client transport with JDBC Uri: jdbc:hive2://localhost:10000: java.net.ConnectException: Connection refused \(Connection refused\) \(state=08S01,code=0\)

