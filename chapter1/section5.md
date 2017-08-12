# jdbc

Java.lang.ClassNotFoundException: org.apache.Hadoop.hive.jdbc.HiveDriver

解决方案：

Class.forName\("org.apache.hive.jdbc.HiveDriver"\);

而不是：

Class.forName\("org.apache.hadoop.hive.jdbc.HiveDriver"\);

