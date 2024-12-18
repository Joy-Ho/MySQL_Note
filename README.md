# MySQL Note

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


