#### mysql

> 查询所有的数据库：show databases;
>
> 查询某个数据库的所有的表：show tables;
>
> 选中某个数据库进行操作：use XXX数据库;
>
> 创建数据库：create database test；
>
> 创建一个数据表：create table XX(id int,name varchar(50));
>
> 查看创建数据表的结构：describe XX；
>
> 退出数据库：exit;
>
> mysql常用数据类型：数值，日期/时间，字符串（字符）类型
>
> **对记录CRUD**
>
> > SQL的查询语句：select * from XX表 where 条件;
> >
> > 添加数据：insert into XX values（1，‘Jerry’）;
> >
> > 删除数据：delete from XX where 条件;
> >
> > 修改数据：update  X表 set 条件 where 条件
>
> **对表增删改**
>
> > 修改表结构，添加主键：alter table XX add primary key(id);
> >
> > 修改表结构，删除主键：alter table XX drop primary key；
> >
> > 使用modify，修改字段：alter table XX modify id int primary key;
>
> **mysql建表约束**
>
> > 主键约束
> >
> > >  lanhezhujia唯一确定一张表中的一条记录（不能重复，不能为空）。
> > >
> > > 单一主键	primary key
> > >
> > > 联合主键，只要联合主键的值加起来不重复就可以，但都不能为空	primary key(字段1，字段2)
> >
> > 自增约束
> >
> > > auto_increment
> >
> > 外键约束
> >
> > > 涉及到两个表
> > >
> > > foreign key(该表的字段) references XX另一张表(另一张表的字段)
> >
> > 唯一约束
> >
> > > 约束该字段的值不能重复
> > >
> > > unique
> >
> > 非空约束
> >
> > > 修饰字段不能为空
> > >
> > > not null
> >
> > 默认约束
> >
> > > 就是插入字段的时候，如果没有传值，就会使用默认值
> > >
> > > default 值
>
> **范式**
>
> > 第一范式 1NF
> >
> > > 字段值还可以继续拆分的就不满足第一范式
> >
> > 第二范式 2NF
> >
> > > 满足第一范式，且除主键外的每一列都必须完全依赖于主键
> >
> > 第三范式 3NF
> >
> > > 满足第二范式，除开主键列的其他列之间不能有传递依赖关系（其他列只能依赖于主键全部）
>
> **其他**
>
> > **排重**：distinct
> >
> > **查询区间**：between ... and ...
> >
> > **直接使用运算符比较**：>,<,...
> >
> > **表示或者关系的查询**：同一个字段：in(value1,value2)；不同的字段：or
> >
> > **升序，降序**：order by XX字段 asc；order by XX字段 desc
> >
> > **统计**：count（*）
> >
> > **最高**：max（字段）
> >
> > **limit** 第一个数字表示从第几个开始，第二个数字表示查询多少条
> >
> > **分组**：group by，后面带条件的话应该用having
> >
> > **平均成绩**：avg(某个字段)
> >
> > **模糊查询**：like
> >
> > **union**：求并集
> >
> > **any**：至少
> >
> > **all**：所有
>
> **事务**
>
> > mysql中，事务其实是一个最小的不可分割的工作单元。事务能够保证一个业务的逻辑型。
> >
> > **事务四大特性**：
> >
> > A	Atomic	原子性：事物是最小的单位，不可以分割
> >
> > C	Consistency	一致性：事务要求，同一事务的sql语句，必须保证同时成功或者同时失败
> >
> > I	Isolation	隔离性：事务a和事务b之间具有隔离性
> >
> > > read uncommitted:读未提交的
> > >
> > > > 如果两个事务都在进行操作，如果一个事务对数据进行操作，操作过程中事务没有被提交，但是他的数据可以被另一个事务读取到，就会出现脏读（一个事务读到另一个事务没有提交的数据）
> > >
> > > read committed:读已经提交的
> > >
> > > > 读同一个表的数据，发现前后不一致，因为事务1在之前已经读过了，这时候事务2对数据进行操作并提交，之后事务1又开始读数据发现两次读取的不一致。
> > > >
> > > > 不可重复读现象
> > >
> > > repeatable read:可以重复读（mysql默认级别）
> > >
> > > > 事务a，b同时操作一张表，事务a提交的数据也不能让被事务b读到。造成幻读
> > >
> > > serializable:串行化
> > >
> > > > 当数据被另一个事务操作的时候，其他事务是不能进行写操作的，会进入排队状态（串行化），直到另一事务结束之后，这个写操作才会执行（在没有等待超时的情况下）
> > > >
> > > > 问题：性能差，隔离级别越高，性能越差
> >
> > D	Durability	持久性：事务一旦结束就不可返回
>
> > **mysql默认开启事务（自动提交）@@autocommit=1**
> >
> > > 默认开启事务的作用：当我们去执行一个sql语句的时候，效果会立即体现出来，且**不能回滚**（rollback）。
> > >
> > > set **autocommit=0**；（即自动提交为false）；当我们去执行一个sql语句的时候，回滚之后能将该语句撤销。想要不被撤销，需要**commit手动提交**，那么即使再回滚就不能再撤销了。
> >
> > **mysql手动开启事务**
> >
> > > @@autocommit=1还是为1；
> > >
> > > 手动开启事务有两种方式：1.begin；2.start transaction；
> > >
> > > 手动开启事务之后，再rollback，还是可以撤销
> >
> > **查看数据库隔离级别**
> >
> > > mysql 8.0:select @@global.transaction_isolation;
> > >
> > > mysql 5.x:select @@global.tx_isolation;
> >
> > **修改数据库隔离级别**
> >
> > > set global transaction isolation level 隔离级别；

