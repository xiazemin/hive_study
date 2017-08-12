# Hive创建数据库

CREATE DATABASE语句



创建数据库是用来创建数据库在Hive中语句。在Hive数据库是一个命名空间或表的集合。此语法声明如下：



CREATE DATABASE\|SCHEMA \[IF NOT EXISTS\] &lt;database name&gt;

在这里，IF NOT EXISTS是一个可选子句，通知用户已经存在相同名称的数据库。可以使用SCHEMA 在DATABASE的这个命令。下面的查询执行创建一个名为userdb数据库：



hive&gt; CREATE DATABASE \[IF NOT EXISTS\] userdb;

或



hive&gt; CREATE SCHEMA userdb;

下面的查询用于验证数据库列表：



hive&gt; SHOW DATABASES;

default

userdb

