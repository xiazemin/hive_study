# 建库实践

hive&gt; create database userdb;

OK

Time taken: 0.216 seconds

hive&gt; show databases;

OK

Failed with exception java.io.IOException:java.lang.IllegalArgumentException: java.net.URISyntaxException: Relative path in absolute URI: ${system:user.name%7D

Time taken: 0.02 seconds

hive&gt;

解决方法：新建文件夹 ../apache-hive-1.2.1-bin/iotmp，进入apache-hive-1.2.1-bin  -&gt;  conf -&gt; hive-site.xml，

添加属性 system:java.io.tmpdir：

&lt;property&gt;

&lt;name&gt;system:java.io.tmpdir&lt;/name&gt;

&lt;value&gt;../apache-hive-1.2.1-bin/iotmp&lt;/value&gt;      \#\#注意这里路径为本机上的绝对路径

&lt;description/&gt;

&lt;/property&gt;



如果还是不行

继续在hive-site.xml中，

将hive.exec.local.scratchdir

     ${system:java.io.tmpdir}/${ system:user.name}

改成：

    hive.exec.local.scratchdir

    ${ java.io.tmpdir}/${ user.name}

