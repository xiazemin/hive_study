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



