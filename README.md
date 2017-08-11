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

