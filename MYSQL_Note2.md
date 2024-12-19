# MySQL Note_2

> Execute sql file
```bash 
source C:/Users/admin/Documents/test.sql;
```
#











> Display all databases.
 
```bash 
show databases;
```
```bash
Result:
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```
#

> Create a database.
 
```bash 
create database db1;
```
#

### Practice: Create a table named employee in demo database
| employeeID  | birth_date | first_name | last_name | gender | hired_date |
| ----------  | ---------- | ---------- | --------- | ------ | ---------- |
| INT | DATE        | VARCHAR(20) | VARCHAR(20) | ENUM('M', 'F') | DATE |


#

```bash 
Result:

desc employees;
+------------+---------------+------+-----+------------+----------------+
| Field      | Type          | Null | Key | Default    | Extra          |
+------------+---------------+------+-----+------------+----------------+
| employeeID | int           | NO   | PRI | NULL       | auto_increment |
| birth_date | date          | NO   |     | NULL       |                |
| first_name | varchar(20)   | NO   |     | NULL       |                |
| last_name  | varchar(20)   | NO   |     | NULL       |                |
| gender     | enum('M','F') | NO   |     | NULL       |                |
| hired_date | date          | NO   |     | 2000-01-01 |                |
+------------+---------------+------+-----+------------+----------------+

```


```bash 


```



```bash 


```

