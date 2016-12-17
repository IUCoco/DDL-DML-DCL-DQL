# DDL-DML-DCL-DQL  
DDL DML DCL DQL语句  
原文链接：http://blog.knowsky.com/221957.htm  
总体解释：  
DML（data manipulation language：它们是SELECT、UPDATE、INSERT、DELETE，就象它的名字一样，这4条命令是用来对数据库里的数据进行操作的语言    
DDL（data definition language）：DDL比DML要多，主要的命令有CREATE、ALTER、DROP等，DDL主要是用在定义或改变表（TABLE）的结构，数据类型，表之间的链接和约束等初始化工作上，他们大多在建立表时使用  
DCL（Data Control Language）：是数据库控制功能。是用来设置或更改数据库用户或角色权限的语句，包括（grant,deny,revoke等）语句。在默认状态下，只有sysadmin,dbcreator,db_owner或db_securityadmin等人员才有权力执行DCL  
DDL is Data Definition Language statements. Some examples:数据定义语言，用于定义和管理 SQL 数据库中的所有对象的语言  
1.CREATE - to create objects in the database 创建  
2.ALTER - alters the structure of the database 修改  
3.DROP - delete objects from the database 删除  
4.TRUNCATE - remove all records from a table, including all spaces allocated for the records are removedTRUNCATE TABLE[Table Name]。  
下面是对Truncate语句在MSSQLServer2000中用法和原理的说明：  
Truncate table 表名 速度快,而且效率高,因为:TRUNCATE TABLE 在功能上与不带 WHERE 子句的 DELETE 语句相同：二者均删除表中的全部行。但 TRUNCATE TABLE 比 DELETE 速度快，且使用的系统和事务日志资源少。  
DELETE 语句每次删除一行，并在事务日志中为所删除的每行记录一项。TRUNCATE TABLE 通过释放存储表数据所用的数据页来删除数据，并且只在事务日志中记录页的释放。  
TRUNCATE TABLE 删除表中的所有行，但表结构及其列、约束、索引等保持不变。新行标识所用的计数值重置为该列的种子。如果想保留标识计数值，请改用 DELETE。如果要删除表定义及其数据，请使用 DROP TABLE 语句。  
对于由 FOREIGN KEY 约束引用的表，不能使用 TRUNCATE TABLE，而应使用不带 WHERE 子句的 DELETE 语句。由于 TRUNCATE TABLE 不记录在日志中，所以它不能激活触发器。  
TRUNCATE TABLE 不能用于参与了索引视图的表。  
5.COMMENT - add comments to the data dictionary 注释  
6.GRANT - gives user's access privileges to database 授权  
7.REVOKE - withdraw access privileges given with the GRANT command 收回已经授予的权限  

DML is Data Manipulation Language statements. Some examples:数据操作语言，SQL中处理数据等操作统称为数据操纵语言  
1.SELECT - retrieve data from the a database 查询  
2.INSERT - insert data into a table 添加  
3.UPDATE - updates existing data within a table 更新  
4.DELETE - deletes all records from a table, the space for the records remain 删除  
5.CALL - call a PL/SQL or Java subprogram  
6.EXPLAIN PLAN - explain access path to data  
Oracle RDBMS执行每一条SQL语句，都必须经过Oracle优化器的评估。所以，了解优化器是如何选择(搜索)路径以及索引是如何被使用的，对优化SQL语句有很大的帮助。Explain可以用来迅速方便地查出对于给定SQL语句中的查询数据是如何得到的即搜索路径(我们通常称为Access Path)。从而使我们选择最优的查询方式达到最大的优化效果。  
7.LOCK TABLE - control concurrency 锁，用于控制并发  

DCL is Data Control Language statements. Some examples:数据控制语言，用来授予或回收访问数据库的某种特权，并控制数据库操纵事务发生的时间及效果，对数据库实行监视等  
COMMIT - save work done 提交  
SAVEPOINT - identify a point in a transaction to which you can later roll back 保存点  
ROLLBACK - restore database to original since the last COMMIT 回滚  
SET TRANSACTION - Change transaction options like what rollback segment to use 设置当前事务的特性，它对后面的事务没有影响．  

http://www.w3school.com.cn/sql/sql_where.asp  

SQL DML 和 DDL  

可以把 SQL 分为两个部分：数据操作语言 (DML) 和 数据定义语言 (DDL)。  

SQL (结构化查询语言)是用于执行查询的语法。但是 SQL 语言也包含用于更新、插入和删除记录的语法。  

查询和更新指令构成了 SQL 的 DML 部分：  

SELECT - 从数据库表中获取数据  
UPDATE - 更新数据库表中的数据  
DELETE - 从数据库表中删除数据  
INSERT INTO - 向数据库表中插入数据  
SQL 的数据定义语言 (DDL) 部分使我们有能力创建或删除表格。我们也可以定义索引（键），规定表之间的链接，以及施加表间的约束。  

SQL 中最重要的 DDL 语句:  

CREATE DATABASE - 创建新数据库  
ALTER DATABASE - 修改数据库  
CREATE TABLE - 创建新表  
ALTER TABLE - 变更（改变）数据库表  
DROP TABLE - 删除表  
CREATE INDEX - 创建索引（搜索键）  
DROP INDEX - 删除索引  
AND 和 OR 运算符  

AND 和 OR 可在 WHERE 子语句中把两个或多个条件结合起来。  

如果第一个条件和第二个条件都成立，则 AND 运算符显示一条记录。  

如果第一个条件和第二个条件中只要有一个成立，则 OR 运算符显示一条记录。  

SELECT * FROM Persons WHERE FirstName='Thomas' AND LastName='Carter'  
ORDER BY 语句    

ORDER BY 语句用于根据指定的列对结果集进行排序。  

ORDER BY 语句默认按照升序对记录进行排序。  

如果您希望按照降序对记录进行排序，可以使用 DESC 关键字。  

以字母顺序显示公司名称（Company），并以数字顺序显示顺序号（OrderNumber）：  

SELECT Company, OrderNumber FROM Orders ORDER BY Company, OrderNumber  
结果：  

Company	OrderNumber  
Apple	4698  
IBM	3532  
W3School	2356  
W3School	6953  
SELECT Company, OrderNumber FROM Orders ORDER BY Company DESC, OrderNumber ASC  
INSERT INTO 语句  

INSERT INTO 语句用于向表格中插入新的行。  

语法  

INSERT INTO 表名称 VALUES (值1, 值2,....)  
我们也可以指定所要插入数据的列：  

INSERT INTO table_name (列1, 列2,...) VALUES (值1, 值2,....)  
SQL 语句：  

INSERT INTO Persons VALUES ('Gates', 'Bill', 'Xuanwumen 10', 'Beijing')  
SQL 语句：  

INSERT INTO Persons (LastName, Address) VALUES ('Wilson', 'Champs-Elysees')  
Update 语句  

Update 语句用于修改表中的数据。  

语法：  

UPDATE 表名称 SET 列名称 = 新值 WHERE 列名称 = 某值  
DELETE 语句  

DELETE 语句用于删除表中的行。  

语法  

DELETE FROM 表名称 WHERE 列名称 = 值  
约束补充：不为空，不能重复、默认值 Navicat  DDL查看  
