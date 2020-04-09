## 作业3：2个query用join写
#### 第一个query
```sql
mysql> select t1.deptno,t1.empno,t1.ename,t1.job,t1.MGR,t1.Hiredate,t1.sal,t1.comm
    ->         from t_employee2 t1 inner join t_employee2 t2
    ->                 on t1.sal>t2.sal and (t2.ename='SMITH');
+--------+-------+--------+-----------+------+------------+------+------+
| deptno | empno | ename  | job       | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+-----------+------+------------+------+------+
|     30 |  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |
|     30 |  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |
|     20 |  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 |  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |
|     10 |  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |
|     20 |  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 |  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |
|     20 |  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |
|     30 |  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |
|     20 |  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |
+--------+-------+--------+-----------+------+------------+------+------+
12 rows in set (0.01 sec)

mysql> select * from t_employee2;
+--------+-------+--------+-----------+------+------------+------+------+
| deptno | empno | ename  | job       | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+-----------+------+------------+------+------+
|     20 |  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |
|     30 |  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |
|     30 |  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |
|     20 |  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 |  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |
|     10 |  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |
|     20 |  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 |  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |
|     20 |  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |
|     30 |  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |
|     20 |  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |
+--------+-------+--------+-----------+------+------------+------+------+
13 rows in set (0.00 sec)

mysql> select * from t_employee2 WHERE sal > (
    -> select sal from t_employee2 WHERE ename='SMITH');
+--------+-------+--------+-----------+------+------------+------+------+
| deptno | empno | ename  | job       | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+-----------+------+------------+------+------+
|     30 |  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |
|     30 |  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |
|     20 |  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 |  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |
|     10 |  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |
|     20 |  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 |  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |
|     20 |  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |
|     30 |  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |
|     20 |  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |
+--------+-------+--------+-----------+------+------------+------+------+
12 rows in set (0.00 sec)
```
![](https://github.com/CNXUXIN/database/blob/master/pictures/work3.1.png?raw=true)

## 第二个query
```sql
mysql> select * from t_employee2 WHERE (sal, job) = (
    -> select sal,job from t_employee2 where ename = 'smith');
+--------+-------+-------+-------+------+------------+------+------+
| deptno | empno | ename | job   | MGR  | Hiredate   | sal  | comm |
+--------+-------+-------+-------+------+------------+------+------+
|     20 |  7369 | SMITH | CLERK | 7902 | 1981-03-12 |  800 | NULL |
+--------+-------+-------+-------+------+------------+------+------+
1 row in set (0.00 sec)

mysql> select t1.deptno,t1.empno,t1.ename,t1.job,t1.MGR,t1.Hiredate,t1.sal,t1.comm
    ->             from t_employee2 t1 inner join t_employee2 t2
    ->                   on (t1.sal = t2.sal and (t2.ename='SMITH')) AND (t1.job = t2.job and (t2.ename='SMITH'));
+--------+-------+-------+-------+------+------------+------+------+
| deptno | empno | ename | job   | MGR  | Hiredate   | sal  | comm |
+--------+-------+-------+-------+------+------------+------+------+
|     20 |  7369 | SMITH | CLERK | 7902 | 1981-03-12 |  800 | NULL |
+--------+-------+-------+-------+------+------------+------+------+
1 row in set (0.00 sec)

mysql> select * from t_employee2;
+--------+-------+--------+-----------+------+------------+------+------+
| deptno | empno | ename  | job       | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+-----------+------+------------+------+------+
|     20 |  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |
|     30 |  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |
|     30 |  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |
|     20 |  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 |  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |
|     10 |  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |
|     20 |  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 |  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |
|     20 |  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |
|     30 |  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |
|     20 |  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |
+--------+-------+--------+-----------+------+------------+------+------+
13 rows in set (0.00 sec)
```
![](https://github.com/CNXUXIN/database/blob/master/pictures/work3.2.png?raw=true)
