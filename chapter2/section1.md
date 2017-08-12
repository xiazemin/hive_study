# section1



NestedThrowables:

java.sql.SQLException: Unable to open a test connection to the given database. JDBC url = jdbc:derby:;databaseName=metastore\_db;create=true, username = APP. Terminating connection pool \(set lazyInit to true if you expect to start your database after your app\). Original Exception: ------

java.sql.SQLException: Failed to start database 'metastore\_db' with class loader sun.misc.Launcher$AppClassLoader@b4c966a, see the next exception for details.

$ vi conf/hive-site.xml

  &lt;property&gt;

    &lt;name&gt;javax.jdo.option.ConnectionUserName&lt;/name&gt;

    &lt;value&gt;APP&lt;/value&gt;

    &lt;description&gt;Username to use against metastore database&lt;/description&gt;

  &lt;/property&gt;

  &lt;property&gt;

    &lt;name&gt;javax.jdo.option.ConnectionPassword&lt;/name&gt;

    &lt;value&gt;mine&lt;/value&gt;

    &lt;description&gt;password to use against metastore database&lt;/description&gt;

  &lt;/property&gt;



