# MySQL Note_1

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

> Remove a database.
 
```bash 
drop database db1;
```
#

> Display the numbers of tables in the specified database.
 
```bash 
use db1;
select database();
```
#

> Create a database first, then specify which database. Next, create a table.

```bash
Create database demo;
use demo;
create table person (name varchar(20), phone varchar(20), age int);
```
#

> Display the description of a table, including field and type. 
```bash 
desc person;
```
#

> Remove a table. Specify which database first.
```bash 
use demo;
drop table person;
show tables;
```
#

### Practice: Create a table named employee in demo database
| employeeID  | birth_date | first_name | last_name | gender | hired_date |
| ----------  | ---------- | ---------- | --------- | ------ | ---------- |
| INT | DATE        | VARCHAR(20) | VARCHAR(20) | ENUM('M', 'F') | DATE |

![image](https://github.com/user-attachments/assets/0ae92b02-507a-408c-8bd7-d96ba42ca02a)
![image](https://github.com/user-attachments/assets/05802e84-6f84-40b5-8025-08fbf3b3d4bc)

#

> Insert new record into **Person** table
```bash
INSERT INTO person(name, phone, age) values ("John", "24566", "25");
```
#
> Select all data from  **Person** table
```bash
SELECT * FROM Person;
```
```bash
Result:
+------+-------+------+
| name | phone | age  |
+------+-------+------+
| John | 24566 |   25 |
+------+-------+------+
```

#
> Select **name** column from  **Person** table
```bash
SELECT name FROM Person;
```
```bash
Result:
+------+
| name |
+------+
| John |
+------+
```

#
> Set default value
```bash
 create table Person_db2(name VARCHAR(20) DEFAULT "Unknown", phone VARCHAR(20), age INT);
 desc Person_db2;
```
```bash
Result:
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| name  | varchar(20) | YES  |     | Unknown |       |
| phone | varchar(20) | YES  |     | NULL    |       |
| age   | int         | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
```

# 
> Set primary key (unique). Set **phone** column as primary key
```bash
Way1:
CREATE TABLE Person_db3(
   name VARCHAR(20),
   phone VARCHAR(20),
   age INT,
   PRIMARY KEY (phone));

Way2:
CREATE TABLE Person_db3(
    name VARCHAR(20),
    phone VARCHAR(20) PRIMARY KEY,
    age INT);

desc Person_db3;
```

```bash
Result:
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| name  | varchar(20) | YES  |     | NULL    |       |
| phone | varchar(20) | NO   | PRI | NULL    |       |
| age   | int         | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
```


# 
> Set primary key of 2 columns. Set **name** and **phone** column as primary key
```bash
CREATE TABLE Person_db3(
    name VARCHAR(20),
    phone VARCHAR(20),
    age INT,
    PRIMARY KEY(name, phone));
```
```bash
Result:
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| name  | varchar(20) | NO   | PRI | NULL    |       |
| phone | varchar(20) | NO   | PRI | NULL    |       |
| age   | int         | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
```

### Practice: Create a table named employees in demo database
| employeeID  | birth_date | first_name | last_name | gender | hired_date |
| ----------  | ---------- | ---------- | --------- | ------ | ---------- |
| INT  | DATE | VARCHAR(20) | VARCHAR(20) | ENUM('M', 'F') | DATE |


```bash 
Requirements:

employeeID: Automatically increments, mandatory, primary key
birth_date: Date, mandatory
first_name: Text, mandatory
last_name: Text, mandatory
gender: mandatory
hired_date: Date, mandatory, Default is "2000-01-01"
```

```bash 
CREATE TABLE employees(
    employeeID INT AUTO_INCREMENT,
    birth_date DATE NOT NULL,
    first_name VARCHAR(20) NOT NULL,
    last_name VARCHAR(20) NOT NULL,
    gender ENUM("M","F") NOT NULL,
    hired_date DATE NOT NULL DEFAULT "2000-01-01",
    PRIMARY KEY (employeeID));
```

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

