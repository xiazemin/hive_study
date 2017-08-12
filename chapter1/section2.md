# hive数据类型

整型

整型数据可以指定使用整型数据类型，INT。当数据范围超过INT的范围，需要使用BIGINT，如果数据范围比INT小，使用SMALLINT。 TINYINT比SMALLINT小。

字符串类型  
字符串类型的数据类型可以使用单引号\(''\)或双引号\(“”\)来指定。它包含两个数据类型：VARCHAR和CHAR。Hive遵循C-类型的转义字符。

时间戳

它支持传统的UNIX时间戳可选纳秒的精度。它支持的java.sql.Timestamp格式“YYYY-MM-DD HH:MM:SS.fffffffff”和格式“YYYY-MM-DD HH:MM:ss.ffffffffff”。

日期

DATE值在年/月/日的格式形式描述 {{YYYY-MM-DD}}.

小数点  
在Hive 小数类型与Java大十进制格式相同。它是用于表示不可改变任意精度。

联合类型



联合是异类的数据类型的集合。可以使用联合创建的一个实例。语法和示例如下：



UNIONTYPE&lt;int, double, array&lt;string&gt;, struct&lt;a:int,b:string&gt;&gt;



{0:1} 

{1:2.0} 

{2:\["three","four"\]} 

{3:{"a":5,"b":"five"}} 

{2:\["six","seven"\]} 

{3:{"a":8,"b":"eight"}} 

{0:9} 

{1:10.0}

