#### 如何查看mysql数据文件存放位置
SHOW VARIABLES LIKE 'datadir';
#### innodb使用uuid和自增主键，哪个好
1. int类型比字符串比较效率高
2. int类型插入数据时可以按页往后连续插入，不需要中间插入；而且查询时磁盘只需要旋转即可，不用寻道
#### [innodb和myisam的区别](https://phoenixnap.com/kb/myisam-vs-innodb#:~:text=MyISAM%20and%20InnoDB%20are%20MySQL%20storage%20engines.%20Storage,of%20MySQL%205.5%2C%20MyISAM%20was%20replaced%20with%20InnoDB.)
Features |	MyISAM	| InnoDB
-------- | ----- | -----------
Type	| Non-Transactional	| Transactional
Locking	| Table locking	| Row-level locking
Foreign keys |	No |	Yes
Table, index, and data storage	| Three separate files (.frm, .myd, and .myi)	| Tablespace
Designed for	| Speed |	Performance
ACID |	No |	Yes

#### 聚簇索引与非聚簇索引
什么是聚簇索引？
很简单记住一句话：找到了索引就找到了需要的数据，那么这个索引就是聚簇索引，所以主键就是聚簇索引，修改聚簇索引其实就是修改主键。

什么是非聚簇索引？
索引的存储和数据的存储是分离的，也就是说找到了索引但没找到数据，需要根据索引上的值(主键)再次回表查询,非聚簇索引也叫做辅助索引。
