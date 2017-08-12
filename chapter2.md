# server2无法连接

&lt;property&gt;

&lt;name&gt;hive.server2.thrift.port&lt;/name&gt;

&lt;value&gt;10000&lt;/value&gt;

&lt;/property&gt;

&lt;property&gt;

&lt;name&gt;hive.server2.thrift.bind.host&lt;/name&gt;

&lt;value&gt;localhost&lt;/value&gt; &lt;!-- 默认是localhost，但我手动改成了本机的ip地址,很可能就是我改了这个才起作用的 --&gt;

&lt;/property&gt;

$ vi ./conf/hive-site.xml

&lt;property&gt;

    &lt;name&gt;hive.log4j.file&lt;/name&gt;

    &lt;value&gt;/Users/didi/hive/hive/iotmp/&lt;/value&gt;

&lt;/property&gt;

