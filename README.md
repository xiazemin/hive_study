# 安装

$  axel -n 20 [http://apache.fayea.com/hive/hive-2.3.0/apache-hive-2.3.0-bin.tar.gz](http://apache.fayea.com/hive/hive-2.3.0/apache-hive-2.3.0-bin.tar.gz)

$ mv apache-hive-2.3.0-bin hive

$ vi .bashrc

export HIVE\_HOME=/Users/didi/hive/hive

export PATH=$PATH:$HIVE\_HOME/bin

export CLASSPATH=$CLASSPATH:/Users/didi/hadoop/hadoop/\*:.

export CLASSPATH=$CLASSPATH:/Users/didi/hive/hive/lib/\*:.

$cd $HIVE\_HOME/conf

$   cp hive-env.sh.template hive-env.sh

$ vi hive-env.sh

export HADOOP\_HOME=/Users/didi/hadoop/hadoop/

Hive安装成功完成。现在，需要一个外部数据库服务器配置Metastore。我们使用Apache Derby数据库。

$ axel -n 60 [http://archive.apache.org/dist/db/derby/db-derby-10.8.2.2/db-derby-10.8.2.2-bin.tar.gz](http://archive.apache.org/dist/db/derby/db-derby-10.8.2.2/db-derby-10.8.2.2-bin.tar.gz)

$ vi .bashrc

export DERBY\_HOME=/Users/didi/hive/derby

export PATH=$PATH:$DERBY\_HOME/bin

export CLASSPATH=$CLASSPATH:$DERBY\_HOME/lib/derby.jar:$DERBY\_HOME/lib/derbytools.jar

$ mkdir $DERBY\_HOME/data

$  cd $HIVE\_HOME/conf

$  cp hive-default.xml.template hive-site.xml

$ vi hive-site.xml

--&gt;&lt;configuration&gt;

&lt;property&gt;

&lt;name&gt;javax.jdo.option.ConnectionURL&lt;/name&gt;

&lt;value&gt;jdbc:derby://localhost:1527/metastore\_db;create=true &lt;/value&gt;

&lt;description&gt;JDBC connect string for a JDBC metastore &lt;/description&gt;

&lt;/property&gt;

创建一个文件名为 jpox.properties 并添加以下行：

javax.jdo.PersistenceManagerFactoryClass =

org.jpox.PersistenceManagerFactoryImpl

org.jpox.autoCreateSchema = false

org.jpox.validateTables = false

org.jpox.validateColumns = false

org.jpox.validateConstraints = false

org.jpox.storeManagerType = rdbms

org.jpox.autoCreateSchema = true

org.jpox.autoStartMechanismMode = checked

org.jpox.transactionIsolation = read\_committed

javax.jdo.option.DetachAllOnCommit = true

javax.jdo.option.NontransactionalRead = true

javax.jdo.option.ConnectionDriverName = org.apache.derby.jdbc.ClientDriver

javax.jdo.option.ConnectionURL = jdbc:derby://hadoop1:1527/metastore\_db;create = true

javax.jdo.option.ConnectionUserName = APP

javax.jdo.option.ConnectionPassword = mine

$ cd $HIVE\_HOME

$ ./bin/hive

Exception in thread "main" java.lang.IllegalArgumentException: java.net.URISyntaxException: Relative path in absolute URI: ${system:java.io.tmpdir%7D/$%7Bsystem:user.name%7D

$mkdir /Users/didi/hive/hive/iotmp

$   vi conf/hive-site.xml

--&gt;&lt;configuration&gt;

&lt;property&gt;

&lt;name&gt;system:java.io.tmpdir&lt;/name&gt;

&lt;value&gt;/Users/didi/hive/hive/iotmp/&lt;/value&gt;

&lt;/property&gt;

$ ./bin/hive

SLF4J: Class path contains multiple SLF4J bindings.

SLF4J: Found binding in \[jar:file:/Users/didi/hive/hive/lib/log4j-slf4j-impl-2.6.2.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: Found binding in \[jar:file:/Users/didi/hadoop/hadoop/share/hadoop/common/lib/slf4j-log4j12-1.7.5.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: See [http://www.slf4j.org/codes.html\#multiple\_bindings](http://www.slf4j.org/codes.html#multiple_bindings) for an explanation.

SLF4J: Actual binding is of type \[org.apache.logging.slf4j.Log4jLoggerFactory\]

Logging initialized using configuration in jar:file:/Users/didi/hive/hive/lib/hive-common-2.3.0.jar!/hive-log4j2.properties Async: true

Hive-on-MR is deprecated in Hive 2 and may not be available in the future versions. Consider using a different execution engine \(i.e. spark, tez\) or using Hive 1.X releases.

hive&gt; show tables;

FAILED: SemanticException org.apache.hadoop.hive.ql.metadata.HiveException: java.lang.RuntimeException: Unable to instantiate org.apache.hadoop.hive.ql.metadata.SessionHiveMetaStoreClient

