##聚集索引和非聚集索引?

###聚集索引定义：

数据行的物理存储顺序和主键的逻辑顺序，一般一个表只有一个聚集索引。

###非聚集索引定义：

索引逻辑顺序和行记录的物理存储顺序不同，一般一个表有多个非聚集索引，非聚集索引分为普通索引、唯一索引、全文索引。

###聚集索引和非聚集索引在使用时候的关系：

聚集索引和非聚集索引的数据结构都是B+树，区别是聚集索引在B+树的叶子存储了完整的行记录，而非聚集索引一般起到辅助作用，通过非聚集索引再回表查询，查询整条行记录。
如果在复合索引查到的行记录中已经包括了要查询的数据，即索引覆盖，那就不需要回表查询。

###聚集索引和非聚集索引使用场景

|      动作描述      | 使用聚集索引 | 使用非聚集索引 |
| :----------------: |:------------: | :--------------: |
|  列经常被分组排序  | 应           | 应             |
| 返回某范围内的数据 | 应           | 不应           |
|  一个或极少不同值  | 不应         | 不应           |
|   小数目的不同值   | 应           | 不应           |
|   大数目的不同值   | 不应         | 应             |
|    频繁更新的列    | 不应         | 应             |
|       外键列       | 应           | 应             |
|       主键列       | 应           | 应             |
|   频繁修改索引列   | 不应         | 应             |
