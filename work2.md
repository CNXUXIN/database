## 建立数据库/查看数据库/删除数据库

```sql

mysql> drop database databasetest;

Query OK, 3 rows affected (0.10 sec)



mysql> create database databasetest;

Query OK, 1 row affected (0.00 sec)



mysql> show databases;

+--------------------+

| Database           |

+--------------------+

| information_schema |

| class1             |

| class2             |

| class_1            |

| class_17060112     |

| company            |

| databasetest       |

| mysql              |

| performance_schema |

+--------------------+

9 rows in set (0.00 sec)

mysql> use databasetest;
Database changed
mysql> drop database class1;
Query OK, 0 rows affected (0.00 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| class2             |
| class_1            |
| class_17060112     |
| company            |
| databasetest       |
| mysql              |
| performance_schema |
+--------------------+
8 rows in set (0.00 sec)
```
![](https://github.com/CNXUXIN/database/blob/master/work1.1.png?raw=true)
![](https://github.com/CNXUXIN/database/blob/master/work1.2.png?raw=true)

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
![](https://github.com/CNXUXIN/database/blob/master/work2.1.png?raw=true)
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
![](https://github.com/CNXUXIN/database/blob/master/work2.2.png?raw=true)
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
# NOT NULL constraint
```sql
mysql> create table t_dept2(
    -> deptno INT NOT NULL,
    -> dname VARCHAR(20) DEFAULT 'cjgong',
    -> loc VARCHAR(40)
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> desc t_dept2;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(11)     | NO   |     | NULL    |       |
| dname  | varchar(20) | YES  |     | cjgong  |       |
| loc    | varchar(40) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```
# UNIQUE constraint
```sql
mysql> create table t_dept3(
    -> deptno INT ,
    -> dname VARCHAR(20) UNIQUE,
    -> loc VARCHAR(40)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> desc t_dept3;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(11)     | YES  |     | NULL    |       |
| dname  | varchar(20) | YES  | UNI | NULL    |       |
| loc    | varchar(40) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```
![](https://github.com/CNXUXIN/database/blob/master/work2.3.png?raw=true)
# PRIMARY KEY constraint
```sql
mysql> create table t_dept4(
    -> deptno INT ,
    -> dname VARCHAR(20),
    -> loc VARCHAR(40),
    -> CONSTRAINT pk_dname PRIMARY KEY(dname)
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> desc t_dept4;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(11)     | YES  |     | NULL    |       |
| dname  | varchar(20) | NO   | PRI | NULL    |       |
| loc    | varchar(40) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```
# Auto increment
```sql
mysql>  CREATE TABLE t_dept5(
    -> deptno INT(20) PRIMARY KEY AUTO_INCREMENT,
    -> dname VARCHAR(20),
    -> loc VARCHAR(40)
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> desc t_dept5;
+--------+-------------+------+-----+---------+----------------+
| Field  | Type        | Null | Key | Default | Extra          |
+--------+-------------+------+-----+---------+----------------+
| deptno | int(20)     | NO   | PRI | NULL    | auto_increment |
| dname  | varchar(20) | YES  |     | NULL    |                |
| loc    | varchar(40) | YES  |     | NULL    |                |
+--------+-------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)
```
![](https://github.com/CNXUXIN/database/blob/master/work2.4.png?raw=true)
# INSERT a record to both tables
```sql
mysql> CREATE TABLE t_dept_2(
    -> deptno INT(20),
    -> dname VARCHAR(20),
    -> loc VARCHAR(40)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> INSERT INTO t_dept (descri_head, deptno, dname, loc, descri) VALUES ("head", 1, "myName", "Hangzhou", "waha");
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO t_dept (descri_head, deptno, dname, loc, descri) VALUES ("head2", NULL, "myName2", "Shanghai", "newPlace");
Query OK, 1 row affected (0.00 sec)

mysql>
mysql> INSERT INTO t_dept_2 (deptno, dname, loc) VALUES (1, "myName_t2", "Hangzhou_t2");
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO t_dept_2 (deptno, dname, loc) VALUES (NULL, "myName_t2", "Hangzhou_t2");
Query OK, 1 row affected (0.00 sec)

mysql> select * from t_dept;
+-------------+--------+---------+----------+----------+
| descri_head | deptno | dname   | loc      | descri   |
+-------------+--------+---------+----------+----------+
| head        |      1 | myName  | Hangzhou | waha     |
| head2       |   NULL | myName2 | Shanghai | newPlace |
| head        |      1 | myName  | Hangzhou | waha     |
| head2       |   NULL | myName2 | Shanghai | newPlace |
+-------------+--------+---------+----------+----------+
4 rows in set (0.00 sec)

mysql> select * from t_dept_2;
+--------+-----------+-------------+
| deptno | dname     | loc         |
+--------+-----------+-------------+
|      1 | myName_t2 | Hangzhou_t2 |
|   NULL | myName_t2 | Hangzhou_t2 |
+--------+-----------+-------------+
2 rows in set (0.00 sec)
```
![](https://github.com/CNXUXIN/database/blob/master/work2.5.png?raw=true)
# Insert records
```sql
mysql> INSERT INTO t_dept (dname, loc) VALUES ("myName_1", "Hangzhou_1");
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO t_dept (dname, loc) VALUES ("myName_2", "Hangzhou_2");
Query OK, 1 row affected (0.01 sec)

mysql> select * from t_dept;
+-------------+--------+----------+------------+----------+
| descri_head | deptno | dname    | loc        | descri   |
+-------------+--------+----------+------------+----------+
| head        |      1 | myName   | Hangzhou   | waha     |
| head2       |   NULL | myName2  | Shanghai   | newPlace |
| head        |      1 | myName   | Hangzhou   | waha     |
| head2       |   NULL | myName2  | Shanghai   | newPlace |
| NULL        |   NULL | myName_1 | Hangzhou_1 | NULL     |
| NULL        |   NULL | myName_2 | Hangzhou_2 | NULL     |
+-------------+--------+----------+------------+----------+
6 rows in set (0.00 sec)
```
![](https://github.com/CNXUXIN/database/blob/master/work2.6.png?raw=true)
