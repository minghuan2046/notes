#### 数据定义语言
###### ALTER TABLE ...（在db.opt文件中）
作用：ALTER TABLE用于更改原有表的结构。例如，您可以增加或删减列，创建或取消索引，更改原有列的类型，或重新命名列或表。您还可以更改表的评注和表的类型。
注意：ALTER TABLE运行时会对原表进行临时复制，在副本上进行更改，然后删除原表，再对新表进行重命名。在执行ALTER TABLE时，其它用户可以阅读原表，但是对表的更新和修改的操作将被延迟，直到新表生成为止。新表生成后，这些更新和修改信息会自动转移到新表上。
###### CREATE DATABASE ...(在db.opt文件中)、

###### CREATE INDEX

###### CREATE TABLE
MyISAM表文件
bl_name.frm
表格式（定义）文件
tbl_name.MYD
数据文件
tbl_name.MYI
索引文件

##### DROP INDEX

##### DROP DATABASE

##### DROP TABLE

##### RENAME TABLE



#### 数据操作语句

#### DO

#### HANDLER

#### INSERT

####  INSERT ... SELECT

####  INSERT DELAYED

#### LOAD DATA INFILE

#### REPLACE
先删除原表中该行记录，然后插入数据，所有值均采用replace中的值，不可引用原来的值。具体算法：
1.尝试把新行插入到表中
2.当因为对于主键或唯一关键字出现重复关键字错误而造成插入失败时：
a.从表中删除含有重复关键字值的冲突行
b.再次尝试把新行插入到表中
