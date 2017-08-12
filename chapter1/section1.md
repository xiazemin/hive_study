# hive 版本过高

参考教程[http://www.yiibai.com/hive/hive\_installation.html](http://www.yiibai.com/hive/hive_installation.html)

$axel -n 20 [https://mirrors.tuna.tsinghua.edu.cn/apache/hive/hive-1.2.2/apache-hive-1.2.2-bin.tar.gz](https://mirrors.tuna.tsinghua.edu.cn/apache/hive/hive-1.2.2/apache-hive-1.2.2-bin.tar.gz)

$ cp hive-default.xml.template hive-site.xml

$ vi hive-site.xml

$ cp hive-env.sh.template hive-env.sh

$vi hive-env.sh

$ vi jpox.properties

$  cd $HADOOP\_HOME

$ ./sbin/start-all.sh

$  cd $SPARK\_HOME

$  ./bin/spark

$  ./sbin/start-all.sh

$  cd $HIVE\_HOME

$  ./bin/hive

\[ERROR\] Terminal initialization failed; falling back to unsupported

java.lang.IncompatibleClassChangeError: Found class jline.Terminal, but interface was expected

原因：

hadoop目录下存在老版本jline:

/hadoop-2.6.0/share/hadoop/yarn/lib：

$    ls /Users/didi/hadoop/hadoop/share/hadoop/yarn/lib/jline-0.9.94.jar

解决：

$ cp /Users/didi/hive/hive/lib/jline-2.12.jar /Users/didi/hadoop/hadoop/share/hadoop/yarn/lib/

$ mv /Users/didi/hadoop/hadoop/share/hadoop/yarn/lib/jline-0.9.94.jar /Users/didi/hadoop/hadoop/share/hadoop/yarn/lib/jline-0.9.94.jar.bak

$ ./bin/hive

ls: /Users/didi/spark/spark/lib/spark-assembly-\*.jar: No such file or directory

17/08/12 11:26:05 WARN conf.HiveConf: HiveConf of name hive.metastore.local does not exist



Logging initialized using configuration in jar:file:/Users/didi/hive/hive/lib/hive-common-1.2.2.jar!/hive-log4j.properties

hive&gt; show tables;

OK

Time taken: 1.128 seconds

安装成功





