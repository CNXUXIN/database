
# Now create a new table
```sql
mysql> create table t_dept (
    ->     deptno INT,
    -> dname  VARCHAR(20),
    -> loc    VARCHAR(40)
    -> );
Query OK, 0 rows affected (0.06 sec)
```
# show the table
```sql
mysql> describe t_dept;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(11)     | YES  |     | NULL    |       |
| dname  | varchar(20) | YES  |     | NULL    |       |
| loc    | varchar(40) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```
# another way to show the table
```sql
mysql> show create table t_dept;
+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table  | Create Table                                                                                                                                                         |
+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| t_dept | CREATE TABLE `t_dept` (
  `deptno` int(11) DEFAULT NULL,
  `dname` varchar(20) DEFAULT NULL,
  `loc` varchar(40) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1 |
+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
```
# delete the table
```sql
mysql> drop table t_dept;
Query OK, 0 rows affected (0.02 sec)
```
# alter table to add a column
```sql
mysql> ALTER TABLE t_dept
    ->     ADD descri VARCHAR(20);
Query OK, 0 rows affected (0.09 sec)
Records: 0  Duplicates: 0  Warnings: 0
mysql> desc t_dept;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(11)     | YES  |     | NULL    |       |
| dname  | varchar(20) | YES  |     | NULL    |       |
| loc    | varchar(40) | YES  |     | NULL    |       |
| descri | varchar(20) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```
#  alter table to add a column in the first column
```sql
mysql> ALTER TABLE t_dept
    ->     ADD descri_head VARCHAR(20) FIRST;
Query OK, 0 rows affected (0.11 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc t_dept;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| descri_head | varchar(20) | YES  |     | NULL    |       |
| deptno      | int(11)     | YES  |     | NULL    |       |
| dname       | varchar(20) | YES  |     | NULL    |       |
| loc         | varchar(40) | YES  |     | NULL    |       |
| descri      | varchar(20) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```
# modify deptno from INT to VARCHAR
```sql
mysql> ALTER TABLE t_dept
    ->      MODIFY deptno VARCHAR(20);
Query OK, 0 rows affected (0.12 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc t_dept;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| descri_head | varchar(20) | YES  |     | NULL    |       |
| deptno      | varchar(20) | YES  |     | NULL    |       |
| dname       | varchar(20) | YES  |     | NULL    |       |
| loc         | varchar(40) | YES  |     | NULL    |       |
| descri      | varchar(20) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```
# from VARCHAR back to INT
```sql
mysql> ALTER TABLE t_dept
    ->      MODIFY deptno INT;
Query OK, 0 rows affected (0.11 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc t_dept;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| descri_head | varchar(20) | YES  |     | NULL    |       |
| deptno      | int(11)     | YES  |     | NULL    |       |
| dname       | varchar(20) | YES  |     | NULL    |       |
| loc         | varchar(40) | YES  |     | NULL    |       |
| descri      | varchar(20) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```
# 
