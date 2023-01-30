+++
title = "MySQL group on update"
date = 2023-01-30
+++

在做 update 的数据处理的时，有些时候需要其他的表的聚合结果，如 sum、group by 等操作，按照直接的想法，如下的方式是不行的。
```SQL
# 这样操作不行的
update table1 t1 left join table2 child on t1.id = child.parent_id set t1.amount = sum(child.amount) = sum(child.amount) where t1.con1 = 'con1' and t1.parent_id is null
```
需要换另外一种方式。
```SQL
update table1 t1,(select parent_id,sum(amount) as amount from table1 where parent_id is not null and con1 ='con1' group by parent_id) as child set t1.amount = child.amountwhere t1.id = child.parent_id
```