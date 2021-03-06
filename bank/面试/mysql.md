1.如何优化数据库查询

（1）不使用select\*，只取需要的字段，节约资源。select\*很可能不会使用覆盖索引。

（2）若已知查询结果只有一条，使用limit1，这样找到记录后就不用扫描剩余的记录了。

（3）like语句，%不要放在最前面。把%放前面，并不走索引。

因为分析器会先预估走索引和不走索引的行扫描数，当数据量大时，分析器会认为不走索引比走索引的效率高。%匹配任意个字符，下划线匹配一个字符。

（4）如果插入数据过多，考虑批量插入。

（5）如果数据量较大，尽量避免同时修改或删除过多数据。

（6）exist & in 的合理利用

in先做子查询，然后将子查询作为主查询的条件。

exists先做主查询，然后将子查询作为条件，来决定主查询的结果是否保留。

要选择最外层循环小的用法，这取决于两个表的大小。

（7）尽可能使用varchar/nvarchar代替char/nchar。（nvarchar是unicode编码）

变长字段存储空间小，可以节省存储空间。对于查询来说，在一个相对较小的字段内搜索，效率更高。

（8）慎用distinct关键字

在查询一个字段或者很少字段时，distinct给查询带来优化效果。但是在字段很多的时候使用，却会大大降低查询效率。

（9）满足SQL需求的前提下，推荐优先使用Inner join（内连接），如果要使用left join，左边表数据结果尽量小，如果有条件尽量放到左边处理。

（10）优化where子句

尽量避免用or连接。可以用union all代替。

尽量避免在where子句中使用!=或<>操作符

尽量避免在where子句中对字段进行表达式操作

where子句中考虑使用默认值代替null

（11）索引

使用联合索引时，注意索引列的顺序，一般遵循最左匹配原则。

考虑在where和order by涉及的列上建立索引，尽量避免全表扫描。

删除冗余和重复索引

索引不适合建在有大量重复数据的字段上，如性别这类型数据库字段：如果索引列有大量重复数据，Mysql查询优化器推算发现不走索引的成本更低，很可能就放弃索引了。

