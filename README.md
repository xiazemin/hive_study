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

