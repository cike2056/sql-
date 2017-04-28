###sqlite3 常用语法

```
命令:
 .mode column 
 .header on 
 备份database :
 在sqlite中:
 .output test_dump.sql
 .dump
 .exit
 离开sqlite:
 sqlite3 test.db .dump > test_dump.sql //备份database
 sqlite3 test.db < test_dump.sql //还原database
语法:
select lastName, firstName from person; 
select distinct lastName from person;//不包含重复值
select * from person where id between 1 and 3;
select * from person where (name='john' or name='Jim') and age >32;//AND 和 OR 可在 WHERE 子语句中把两个或多个条件结合起来
select * from person order by name desc , id asc;
update person set name='Gates' where id = 5;
delete from person where id = 6;//DELETE 语句用于删除表中的行。
delete from person;//删除所有的行
attach database 'test.db' as 'test_alias';//附加数据库
detach database 'test_alias';//分离数据库
insert into man select * from StudentTable;//使用一个表来填充另一个表
insert into man values(1,'xx',23),(2,'zz',33);
SELECT * FROM COMPANY WHERE AGE IS NOT NULL;
select * from person where name like '%n%';//百分号（%）代表零个、一个或多个数字或字符。下划线（_）代表一个单一的数字或字符。
SELECT * FROM COMPANY WHERE NAME GLOB 'Ki*';//区分大小写.星号（*）代表零个、一个或多个数字或字符。问号（?）代表一个单一的数字或字符。
SELECT * FROM COMPANY WHERE AGE IN ( 25, 27 );
SELECT * FROM COMPANY WHERE AGE NOT IN ( 25, 27 );
SELECT * FROM COMPANY WHERE AGE BETWEEN 25 AND 27;
select * from person where id >(select id from person where age >30);//第一个age>30的id,比这个id大其他
//EXISTS 运算符用于在满足一定条件的指定表中搜索行的存在。
select age from person where exists (select age from person where id >2); //注意:满足子句条件的整个表中搜索.
SELECT count(*) AS '# of cars' FROM Cars;
SELECT count(DISTINCT Customer) AS '# of customers' FROM Orders;
select * from man limit 1,3;
select * from man limit 3;
.nullvalue NULL //how sqlite3 shows NULL values
SELECT last_insert_rowid();
SELECT avg(Price) AS 'Average price' FROM Cars;
SELECT sum(OrderPrice) AS Sum FROM Orders;
select date();//可选参数
select datetime();//可选参数
select id from person limit 10 offset 10;//从11开始,共10个
select id from person order by id desc limit 10 offset 4;//先排序,再圈范围
select name ,sum(age) from person group by name order by upper(name);
SELECT * FROM COMPANY GROUP BY name HAVING count(name) < 2;//和group by 搭配使用.use a HAVING clause without the GROUP BY clause, the HAVING clause behaves like a WHERE clause.
alter table person add column Address text;//table添加column,sqlite中drop无作用
drop table man;//删除表
alter table person rename to PersonTable;//修改table name

sqlite 函数
SELECT abs(11), abs(-5), abs(0), abs(NULL);
SELECT max(Price), min(Price) FROM Cars;
SELECT upper(Name) AS 'Names in capitals' FROM Friends;
SELECT lower(Name) AS 'Names in lowercase' FROM Friends;
SELECT length('ZetCode');
select * from person where length(name)>4;
SELECT total_changes() AS 'Total changes';// return the number of row changes caused by INSERT, UPDATE, or DELETE statements since the current database connection was opened.
SELECT typeof(12), typeof('ZetCode'), typeof(33.2), typeof(NULL);

```




