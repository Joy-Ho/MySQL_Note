# MySQL Note

> Display all databases.
 
```bash 
show databases;
```

![image](https://github.com/user-attachments/assets/104ba31a-17c5-49ca-b27d-f5414e0641e5)
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

![image](https://github.com/user-attachments/assets/34c1e8cb-b6a0-4aae-83cb-009b3d2d6a97)

![image](https://github.com/user-attachments/assets/e21cb20b-8051-4c09-98a0-c1622b04c843)
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
![image](https://github.com/user-attachments/assets/ad557174-bfbd-42cf-92b9-0a7e58e5b314)
#

## Practice: Create a table named employee in demo database
| employeeID  | birth_date | first_name | last_name | gender | hired_date |
| ----------  | ---------- | ---------- | --------- | ------ | ---------- |
| INT | DATE        | VARCHAR(20) | VARCHAR(20) | ENUM('M', 'F') | DATE |
![image](https://github.com/user-attachments/assets/0ae92b02-507a-408c-8bd7-d96ba42ca02a)
![image](https://github.com/user-attachments/assets/05802e84-6f84-40b5-8025-08fbf3b3d4bc)

#




