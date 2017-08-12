# hive 创建索引

0: jdbc:hive2://localhost:10000/&gt; CREATE INDEX inedx\_key ON TABLE userdb \( key \)  as 'org.apache.hive2.ql.index.compact.CompactIndexHandler';

FAILED: Execution Error, return code 1 from org.apache.hadoop.hive.ql.exec.DDLTask. java.lang.RuntimeException: Please specify deferred rebuild using " WITH DEFERRED REBUILD ".



0: jdbc:hive2://localhost:10000/&gt; CREATE INDEX inedx\_key ON TABLE userdb \( key \)  as 'org.apache.hadoop.hive.ql.index.compact.CompactIndexHandler'  WITH DEFERRED REBUILD;

No rows affected \(0.136 seconds\)

0: jdbc:hive2://localhost:10000/&gt;  SHOW FORMATTED INDEX ON userdb;

+-----------------------+-----------------------+-----------------------+------------------------------+-----------------------+-----------------------+--+

\|       idx\_name        \|       tab\_name        \|       col\_names       \|         idx\_tab\_name         \|       idx\_type        \|        comment        \|

+-----------------------+-----------------------+-----------------------+------------------------------+-----------------------+-----------------------+--+

\| idx\_name              \| tab\_name              \| col\_names             \| idx\_tab\_name                 \| idx\_type              \| comment               \|

\|                       \| NULL                  \| NULL                  \| NULL                         \| NULL                  \| NULL                  \|

\|                       \| NULL                  \| NULL                  \| NULL                         \| NULL                  \| NULL                  \|

\| inedx\_key             \| userdb                \| key                   \| default\_\_userdb\_inedx\_key\_\_  \| compact               \|                       \|

+-----------------------+-----------------------+-----------------------+------------------------------+-----------------------+-----------------------+--+

4 rows selected \(0.109 seconds\)

