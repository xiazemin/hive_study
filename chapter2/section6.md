# ALTER TABLE

0: jdbc:hive2://localhost:10000/&gt; ALTER TABLE userdb ADD COLUMS \(Birthday date,name string\);

Error: Error while compiling statement: FAILED: ParseException line 1:19 cannot recognize input near 'ADD' 'COLUMS' '\(' in alter table statement \(state=42000,code=40000\)

0: jdbc:hive2://localhost:10000/&gt; ALTER TABLE userdb ADD COLUMNS \(

0: jdbc:hive2://localhost:10000/&gt; Birthday date,name string\);

No rows affected \(0.096 seconds\)

0: jdbc:hive2://localhost:10000/&gt;

0: jdbc:hive2://localhost:10000/&gt; select \* from userdb ;

+-------------+---------------+--------------+------------------+--------------+--+

\| userdb.key  \| userdb.value  \| userdb.dept  \| userdb.birthday  \| userdb.name  \|

+-------------+---------------+--------------+------------------+--------------+--+

\| 1213        \| hello         \| NULL         \| NULL             \| NULL         \|

\| 1214        \| hello         \| NULL         \| NULL             \| NULL         \|

\| 1215        \| world         \| NULL         \| NULL             \| NULL         \|

+-------------+---------------+--------------+------------------+--------------+--+

3 rows selected \(0.098 seconds\)

0: jdbc:hive2://localhost:10000/&gt;   update userdb set birthday='2017-08-12 12:00:03';

Error: Error while compiling statement: FAILED: SemanticException \[Error 10294\]: Attempt to do update or delete using transaction manager that does not support these operations. \(state=42000,code=10294\)

