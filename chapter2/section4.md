# hive 分区

Hive组织表到分区。它是将一个表到基于分区列，如日期，城市和部门的值相关方式。使用分区，很容易对数据进行部分查询。

表或分区是细分成桶，以提供额外的结构，可以使用更高效的查询的数据。桶的工作是基于表的一些列的散列函数值。

例如，一个名为Tab1表包含雇员数据，如 id, name, dept 和yoj \(即加盟年份\)。假设需要检索所有在2012年加入，查询搜索整个表所需的信息员工的详细信息。但是，如果用年份分区雇员数据并将其存储在一个单独的文件，它减少了查询处理时间。

添加分区



可以通过添加分区表改变所述表。假设我们有一个表叫employee ，拥有如 Id, Name, Salary, Designation, Dept, 和 yoj等字段。



语法：



ALTER TABLE table\_name ADD \[IF NOT EXISTS\] PARTITION partition\_spec

\[LOCATION 'location1'\] partition\_spec \[LOCATION 'location2'\] ...;



partition\_spec:

: \(p\_column = p\_col\_value, p\_column = p\_col\_value, ...\)

以下查询用于将分区添加到employee表。



hive&gt; ALTER TABLE employee

&gt; ADD PARTITION \(year=’2013’\)

&gt; location '/2012/part2012';

重命名分区



此命令的语法如下。



ALTER TABLE table\_name PARTITION partition\_spec RENAME TO PARTITION partition\_spec;

以下查询用来命名一个分区：

