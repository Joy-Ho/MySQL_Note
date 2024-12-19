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
> Delete data where the salary is 7200.
```bash 
delete from employee where salary=7200;
```

#
> Concat strings, concat first_name and last_name
```bash 
select CONCAT(first_name, " ", last_name, " was hired on ", SUBSTRING(hire_date,1, 4)) as information from employee;
```
```bash
Result:
+------------------------------------+
| information                        |
+------------------------------------+
| Robin Jackman was hired on 2001    |
| Taylor Edward was hired on 2002    |
| Vivian Dickens was hired on 2012   |
| Harry Clifford was hired on 2015   |
| Eliza Clifford was hired on 1998   |
| Nancy Newman was hired on 2007     |
| Melinda Clifford was hired on 2013 |
| Jack Chan was hired on 2018        |
| Harley Gilbert was hired on 2000   |
+------------------------------------+
```

> Concat first name, last name and hired_date.
```bash 
select CONCAT(first_name, ",", last_name) as fullname from employee;
```
```bash
Result:
+------------------+
| fullname         |
+------------------+
| Robin,Jackman    |
| Taylor,Edward    |
| Vivian,Dickens   |
| Harry,Clifford   |
| Eliza,Clifford   |
| Nancy,Newman     |
| Melinda,Clifford |
| Jack,Chan        |
| Harley,Gilbert   |
+------------------+
```
#
> Concat strings with delimeter using **CONCAT_WS**
```bash
select CONCAT_WS("-", first_name, last_name, title) from employee;
```

```bash
Result:
+----------------------------------------------+
| CONCAT_WS("-", first_name, last_name, title) |
+----------------------------------------------+
| Robin-Jackman-Software Engineer              |
| Taylor-Edward-Software Architect             |
| Vivian-Dickens-Database Administrator        |
| Harry-Clifford-Database Administrator        |
| Eliza-Clifford-Software Engineer             |
| Nancy-Newman-Software Engineer               |
| Melinda-Clifford-Project Manager             |
| Jack-Chan-Test Engineer                      |
| Harley-Gilbert-Software Architect            |
+----------------------------------------------+
```

#
> Extract characters from a string using **SUBSTRING**
```bash
select SUBSTRING(title, 1, 5) from employee;
```

```bash
Result:
+------------------------+
| SUBSTRING(title, 1, 5) |
+------------------------+
| Softw                  |
| Softw                  |
| Datab                  |
| Datab                  |
| Softw                  |
| Softw                  |
| Proje                  |
| Test                   |
| Softw                  |
+------------------------+
```

#
> Replace software with hardware
```bash
select first_name, last_name, REPLACE(title, "Software", "Hardware") from employee;
```

```bash
Result:
+------------+-----------+----------------------------------------+
| first_name | last_name | REPLACE(title, "Software", "Hardware") |
+------------+-----------+----------------------------------------+
| Robin      | Jackman   | Hardware Engineer                      |
| Taylor     | Edward    | Hardware Architect                     |
| Vivian     | Dickens   | Database Administrator                 |
| Harry      | Clifford  | Database Administrator                 |
| Eliza      | Clifford  | Hardware Engineer                      |
| Nancy      | Newman    | Hardware Engineer                      |
| Melinda    | Clifford  | Project Manager                        |
| Jack       | Chan      | Test Engineer                          |
| Harley     | Gilbert   | Hardware Architect                     |
+------------+-----------+----------------------------------------+
```

#
> uppercase
```bash
select UPPER(first_name) as FirstName, UPPER(last_name) as LastName from employee;
```

```bash
Result:
+-----------+----------+
| FirstName | LastName |
+-----------+----------+
| ROBIN     | JACKMAN  |
| TAYLOR    | EDWARD   |
| VIVIAN    | DICKENS  |
| HARRY     | CLIFFORD |
| ELIZA     | CLIFFORD |
| NANCY     | NEWMAN   |
| MELINDA   | CLIFFORD |
| JACK      | CHAN     |
| HARLEY    | GILBERT  |
+-----------+----------+
```


