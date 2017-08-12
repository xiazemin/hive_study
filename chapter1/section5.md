# jdbc

Java.lang.ClassNotFoundException: org.apache.Hadoop.hive.jdbc.HiveDriver

解决方案：

Class.forName\("org.apache.hive.jdbc.HiveDriver"\);

而不是：

Class.forName\("org.apache.hadoop.hive.jdbc.HiveDriver"\);

引入hive／lib下的jar包

Exception in thread "main" java.sql.SQLException: No suitable driver found for jdbc:hive://localhost:10002/default

	at java.sql.DriverManager.getConnection\(DriverManager.java:689\)

	at java.sql.DriverManager.getConnection\(DriverManager.java:247\)

	at jdbc.main\(jdbc.java:33\)



