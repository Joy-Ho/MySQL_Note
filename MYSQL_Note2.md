# MySQL Note_2

> Execute sql file
```bash 
source C:/Users/admin/Documents/data.sql;
```

```bash
It creates an Employee Table as below:
+----+------------+-----------+------------------------+--------+------------+-------+
| id | first_name | last_name | title                  | salary | hire_date  | notes |
+----+------------+-----------+------------------------+--------+------------+-------+
|  1 | Robin      | Jackman   | Software Engineer      |   5500 | 2001-10-12 | NULL  |
|  2 | Taylor     | Edward    | Software Architect     |   7200 | 2002-09-21 | NULL  |
|  3 | Vivian     | Dickens   | Database Administrator |   6000 | 2012-08-29 | NULL  |
|  4 | Harry      | Clifford  | Database Administrator |   6800 | 2015-12-10 | NULL  |
|  5 | Eliza      | Clifford  | Software Engineer      |   4750 | 1998-10-19 | NULL  |
|  6 | Nancy      | Newman    | Software Engineer      |   5100 | 2007-01-23 | NULL  |
|  7 | Melinda    | Clifford  | Project Manager        |   8500 | 2013-10-29 | NULL  |
|  8 | Jack       | Chan      | Test Engineer          |   6500 | 2018-09-07 | NULL  |
|  9 | Harley     | Gilbert   | Software Architect     |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+------------------------+--------+------------+-------+
```

#
> Select data from a table, select **first_name** and **last_name** from **Employee** table.
```bash 
select first_name, last_name from employee;
```

```bash
Result:
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Robin      | Jackman   |
| Taylor     | Edward    |
| Vivian     | Dickens   |
| Harry      | Clifford  |
| Eliza      | Clifford  |
| Nancy      | Newman    |
| Melinda    | Clifford  |
| Jack       | Chan      |
| Harley     | Gilbert   |
+------------+-----------+
```

#
> Extract data that satisfies a condition where the title is Database Administrator.
```bash 
select * from employee where title="Database Administrator";
```
```bash
Result:
+----+------------+-----------+------------------------+--------+------------+-------+
| id | first_name | last_name | title                  | salary | hire_date  | notes |
+----+------------+-----------+------------------------+--------+------------+-------+
|  3 | Vivian     | Dickens   | Database Administrator |   6000 | 2012-08-29 | NULL  |
|  4 | Harry      | Clifford  | Database Administrator |   6800 | 2015-12-10 | NULL  |
+----+------------+-----------+------------------------+--------+------------+-------+
```

> Extract data that satisfies a condition where the salary is 8500.
```bash 
select * from employee where salary=8500;
```
```bash
Result:
+----+------------+-----------+-----------------+--------+------------+-------+
| id | first_name | last_name | title           | salary | hire_date  | notes |
+----+------------+-----------+-----------------+--------+------------+-------+
|  7 | Melinda    | Clifford  | Project Manager |   8500 | 2013-10-29 | NULL  |
+----+------------+-----------+-----------------+--------+------------+-------+
```

> Extract data that satisfies 2 conditions where the title is Software Architect or the salary is 6000.
```bash 
select * from employee where title="Software Architect" or salary=6000;
```
```bash
Result:
+----+------------+-----------+------------------------+--------+------------+-------+
| id | first_name | last_name | title                  | salary | hire_date  | notes |
+----+------------+-----------+------------------------+--------+------------+-------+
|  2 | Taylor     | Edward    | Software Architect     |   7200 | 2002-09-21 | NULL  |
|  3 | Vivian     | Dickens   | Database Administrator |   6000 | 2012-08-29 | NULL  |
|  9 | Harley     | Gilbert   | Software Architect     |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+------------------------+--------+------------+-------+
```
#
> Extract data that does not satisfy a condition where the salary is 8500.
```bash 
select * from employee where NOT salary=8500;
```
```bash
Result:
+----+------------+-----------+------------------------+--------+------------+-------+
| id | first_name | last_name | title                  | salary | hire_date  | notes |
+----+------------+-----------+------------------------+--------+------------+-------+
|  1 | Robin      | Jackman   | Software Engineer      |   5500 | 2001-10-12 | NULL  |
|  2 | Taylor     | Edward    | Software Architect     |   7200 | 2002-09-21 | NULL  |
|  3 | Vivian     | Dickens   | Database Administrator |   6000 | 2012-08-29 | NULL  |
|  4 | Harry      | Clifford  | Database Administrator |   6800 | 2015-12-10 | NULL  |
|  5 | Eliza      | Clifford  | Software Engineer      |   4750 | 1998-10-19 | NULL  |
|  6 | Nancy      | Newman    | Software Engineer      |   5100 | 2007-01-23 | NULL  |
|  8 | Jack       | Chan      | Test Engineer          |   6500 | 2018-09-07 | NULL  |
|  9 | Harley     | Gilbert   | Software Architect     |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+------------------------+--------+------------+-------+
```

#
> Update data, the salary of Software Architect update to 20000, and update the notes
```bash 
update employee set salary=20000, notes="update" where title="Software Architect";
```
```bash
Result:
select * from employee where title="Software Architect";
+----+------------+-----------+--------------------+--------+------------+--------+
| id | first_name | last_name | title              | salary | hire_date  | notes  |
+----+------------+-----------+--------------------+--------+------------+--------+
|  2 | Taylor     | Edward    | Software Architect |  20000 | 2002-09-21 | update |
|  9 | Harley     | Gilbert   | Software Architect |  20000 | 2000-07-17 | update |
+----+------------+-----------+--------------------+--------+------------+--------+
```


#
#
#
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

