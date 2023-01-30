+++
title = "MySQL Insert From Select"
date = 2023-01-30
+++

在做数据处理插入新数据的时候，经常需要从其他表拿数据，可以直接 SQL 实现。
```SQL
insert into target_table(col1,col2) select t1.name as col1,t2.name as col2 from table1 t1 left join table2 t2 on t1.t2_id = t2.id where t1.name = 'xxx'
```
