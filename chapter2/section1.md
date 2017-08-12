# section1

NestedThrowables:

java.sql.SQLException: Unable to open a test connection to the given database. JDBC url = jdbc:derby:;databaseName=metastore\_db;create=true, username = APP. Terminating connection pool \(set lazyInit to true if you expect to start your database after your app\). Original Exception: ------

java.sql.SQLException: Failed to start database 'metastore\_db' with class loader sun.misc.Launcher$AppClassLoader@b4c966a, see the next exception for details.

$ vi conf/hive-site.xml

&lt;property&gt;

```
&lt;name&gt;javax.jdo.option.ConnectionUserName&lt;/name&gt;

&lt;value&gt;APP&lt;/value&gt;

&lt;description&gt;Username to use against metastore database&lt;/description&gt;
```

&lt;/property&gt;

&lt;property&gt;

```
&lt;name&gt;javax.jdo.option.ConnectionPassword&lt;/name&gt;

&lt;value&gt;mine&lt;/value&gt;

&lt;description&gt;password to use against metastore database&lt;/description&gt;
```

&lt;/property&gt;

$ hive --service hiveserver2

$     beeline

Beeline version 1.2.1.spark2 by Apache Hive

beeline&gt; show tables;

No current connection

beeline&gt;  !connect jdbc:hive2://localhost:10000/ hive.server2.proxy.user=APP -d  org.apache.hive.jdbc.HiveDriver

Connecting to jdbc:hive2://localhost:10000/

17/08/12 18:07:04 INFO jdbc.Utils: Supplied authorities: localhost:10000

17/08/12 18:07:04 INFO jdbc.Utils: Resolved authority: localhost:10000

17/08/12 18:07:04 INFO jdbc.HiveConnection: Will try to open client transport with JDBC Uri: jdbc:hive2://localhost:10000/

Connected to: Apache Hive \(version 1.2.2\)

Driver: Hive JDBC \(version 1.2.1.spark2\)

Transaction isolation: TRANSACTION\_REPEATABLE\_READ

0: jdbc:hive2://localhost:10000/&gt; show tables;

+-----------+--+

\| tab\_name  \|

+-----------+--+

+-----------+--+

No rows selected \(1.776 seconds\)

0: jdbc:hive2://localhost:10000/&gt;

