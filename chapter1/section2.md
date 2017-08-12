hive数据类型
整型
整型数据可以指定使用整型数据类型，INT。当数据范围超过INT的范围，需要使用BIGINT，如果数据范围比INT小，使用SMALLINT。 TINYINT比SMALLINT小。



下表描述了各种INT数据类型：



类型	后缀	示例

TINYINT	Y	10Y

SMALLINT	S	10S

INT	-	10

BIGINT	L	10L

字符串类型



字符串类型的数据类型可以使用单引号\(''\)或双引号\(“”\)来指定。它包含两个数据类型：VARCHAR和CHAR。Hive遵循C-类型的转义字符。



下表描述了各种CHAR数据类型：



数据类型	长度

VARCHAR	1 to 65355

CHAR	255

时间戳



它支持传统的UNIX时间戳可选纳秒的精度。它支持的java.sql.Timestamp格式“YYYY-MM-DD HH:MM:SS.fffffffff”和格式“YYYY-MM-DD HH:MM:ss.ffffffffff”。



日期



DATE值在年/月/日的格式形式描述 {{YYYY-MM-DD}}.



小数点



在Hive 小数类型与Java大十进制格式相同。它是用于表示不可改变任意精度。语法和示例如下：





 

DECIMAL\(precision, scale\)

decimal\(10,0\)

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

文字



下面是Hive中使用的文字中：



浮点类型



浮点类型是只不过有小数点的数字。通常，这种类型的数据组成DOUBLE数据类型。



十进制类型



十进制数据类型是只不过浮点值范围比DOUBLE数据类型更大。十进制类型的范围大约是 -10-308 到 10308.

Null 值



缺少值通过特殊值 - NULL表示。



复杂类型



Hive复杂数据类型如下：



数组



在Hive 数组与在Java中使用的方法相同。



Syntax: ARRAY&lt;data\_type&gt;

映射



映射在Hive类似于Java的映射。



Syntax: MAP&lt;primitive\_type, data\_type&gt;

结构体



在Hive结构体类似于使用复杂的数据。



Syntax: STRUCT&lt;col\_name : data\_type \[COMMENT col\_comment\], ...&gt;

