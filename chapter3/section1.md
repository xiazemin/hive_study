# 分区

0: jdbc:hive2://localhost:10000/&gt; ALTER table userdb

0: jdbc:hive2://localhost:10000/&gt; add partition \(year='2017'\)

0: jdbc:hive2://localhost:10000/&gt; location '/2017/part2017';

Error: Error while compiling statement: FAILED: ValidationFailureSemanticException table is not partitioned but partition spec exists: {year=2017} \(state=42000,code=40000\)

由于在新建表的时候，并没有创建分区列address，所以只有在存在分区列的表上执行增加分区的操作，才会成功。

hive中关于partition的操作：

hive&gt; create table mp \(a string\) partitioned by \(b string, c string\);

OK

Time taken: 0.044 seconds

hive&gt; alter table mp add partition \(b='1', c='1'\);

OK

Time taken: 0.079 seconds

hive&gt; alter table mp add partition \(b='1', c='2'\);

OK

Time taken: 0.052 seconds

hive&gt; alter table mp add partition \(b='2', c='2'\);

OK

Time taken: 0.056 seconds

hive&gt; show partitions mp ;

OK

b=1/c=1

b=1/c=2

b=2/c=2

Time taken: 0.046 seconds

hive&gt; explain extended alter table mp drop partition \(b='1'\);

OK

