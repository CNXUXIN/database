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
