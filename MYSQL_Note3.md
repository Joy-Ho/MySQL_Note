# MySQL Note_2

> **Equal**/**NotEqual**, select data where salary is 8000
```bash 
select * from employee where salary = 8000;
```

```bash
Result:
+----+------------+-----------+--------------------+--------+------------+-------+
| id | first_name | last_name | title              | salary | hire_date  | notes |
+----+------------+-----------+--------------------+--------+------------+-------+
|  9 | Harley     | Gilbert   | Software Architect |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+--------------------+--------+------------+-------+
```

> Equal / NotEqual, select data where salary is not equal to 8000
```bash
way1:
select * from employee where NOT salary = 8000;

way2:
select * from employee where salary != 8000;
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
|  7 | Melinda    | Clifford  | Project Manager        |   8500 | 2013-10-29 | NULL  |
|  8 | Jack       | Chan      | Test Engineer          |   6500 | 2018-09-07 | NULL  |
+----+------------+-----------+------------------------+--------+------------+-------+
```

#
> **LIKE**/**NOT LIKE**, select data where last name contains Cl
```bash 
select * from employee where last_name like "%Cl%";
```

```bash
Result:
+----+------------+-----------+------------------------+--------+------------+-------+
| id | first_name | last_name | title                  | salary | hire_date  | notes |
+----+------------+-----------+------------------------+--------+------------+-------+
|  4 | Harry      | Clifford  | Database Administrator |   6800 | 2015-12-10 | NULL  |
|  5 | Eliza      | Clifford  | Software Engineer      |   4750 | 1998-10-19 | NULL  |
|  7 | Melinda    | Clifford  | Project Manager        |   8500 | 2013-10-29 | NULL  |
+----+------------+-----------+------------------------+--------+------------+-------+
```

#
> LIKE/NOT LIKE, select data where last name does not start with C
```bash 
select * from employee where last_name not like "C%";
```

```bash
Result:
+----+------------+-----------+------------------------+--------+------------+-------+
| id | first_name | last_name | title                  | salary | hire_date  | notes |
+----+------------+-----------+------------------------+--------+------------+-------+
|  1 | Robin      | Jackman   | Software Engineer      |   5500 | 2001-10-12 | NULL  |
|  2 | Taylor     | Edward    | Software Architect     |   7200 | 2002-09-21 | NULL  |
|  3 | Vivian     | Dickens   | Database Administrator |   6000 | 2012-08-29 | NULL  |
|  6 | Nancy      | Newman    | Software Engineer      |   5100 | 2007-01-23 | NULL  |
|  9 | Harley     | Gilbert   | Software Architect     |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+------------------------+--------+------------+-------+
```

#
> greater than/ less than, select data where salary is greater than 7000 
```bash 
select * from employee where salary > 7000;
```

```bash
Result:
+----+------------+-----------+--------------------+--------+------------+-------+
| id | first_name | last_name | title              | salary | hire_date  | notes |
+----+------------+-----------+--------------------+--------+------------+-------+
|  2 | Taylor     | Edward    | Software Architect |   7200 | 2002-09-21 | NULL  |
|  7 | Melinda    | Clifford  | Project Manager    |   8500 | 2013-10-29 | NULL  |
|  9 | Harley     | Gilbert   | Software Architect |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+--------------------+--------+------------+-------+
```

#
> **AND**/**OR**, select data where salary is greater than 7000 and title starts with Software 
```bash 
select * from employee where salary > 7000 and title like "Software%";
```

```bash
Result:
+----+------------+-----------+--------------------+--------+------------+-------+
| id | first_name | last_name | title              | salary | hire_date  | notes |
+----+------------+-----------+--------------------+--------+------------+-------+
|  2 | Taylor     | Edward    | Software Architect |   7200 | 2002-09-21 | NULL  |
|  9 | Harley     | Gilbert   | Software Architect |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+--------------------+--------+------------+-------+
```

#
> **BETWEEN** , select data where salary is greater than 7000 and lower than 8000 
```bash 
select * from employee where salary between 7000 and 8000;
```

```bash
Result:
+----+------------+-----------+--------------------+--------+------------+-------+
| id | first_name | last_name | title              | salary | hire_date  | notes |
+----+------------+-----------+--------------------+--------+------------+-------+
|  2 | Taylor     | Edward    | Software Architect |   7200 | 2002-09-21 | NULL  |
|  9 | Harley     | Gilbert   | Software Architect |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+--------------------+--------+------------+-------+
```

#
>  **IN**/**NOT IN**, select data where title is Test Engineer or Software Architect
```bash 
select * from employee where title in ("Test Engineer", "Software Architect");
```

```bash
Result:
+----+------------+-----------+--------------------+--------+------------+-------+
| id | first_name | last_name | title              | salary | hire_date  | notes |
+----+------------+-----------+--------------------+--------+------------+-------+
|  2 | Taylor     | Edward    | Software Architect |   7200 | 2002-09-21 | NULL  |
|  8 | Jack       | Chan      | Test Engineer      |   6500 | 2018-09-07 | NULL  |
|  9 | Harley     | Gilbert   | Software Architect |   8000 | 2000-07-17 | NULL  |
+----+------------+-----------+--------------------+--------+------------+-------+
```

# 
>  **CASE**, return a value when the condition meets
```bash 
SELECT first_name, last_name, title, salary,
    case
        when salary>=7000 then "high"
        else 'low'
    end as tag
from employee;
```

```bash
Result:
source C:\Users\admin\Documents\case.sql
+------------+-----------+------------------------+--------+------+
| first_name | last_name | title                  | salary | tag  |
+------------+-----------+------------------------+--------+------+
| Robin      | Jackman   | Software Engineer      |   5500 | low  |
| Taylor     | Edward    | Software Architect     |   7200 | high |
| Vivian     | Dickens   | Database Administrator |   6000 | low  |
| Harry      | Clifford  | Database Administrator |   6800 | low  |
| Eliza      | Clifford  | Software Engineer      |   4750 | low  |
| Nancy      | Newman    | Software Engineer      |   5100 | low  |
| Melinda    | Clifford  | Project Manager        |   8500 | high |
| Jack       | Chan      | Test Engineer          |   6500 | low  |
| Harley     | Gilbert   | Software Architect     |   8000 | high |
+------------+-----------+------------------------+--------+------+
```

> +order by salary
```bash 
SELECT first_name, last_name, title, salary,
    case
        when salary>=7000 then "high"
        else 'low'
    end as tag
from employee order by salary desc;
```

```bash
Result:
source C:\Users\admin\Documents\case.sql
+------------+-----------+------------------------+--------+------+
| first_name | last_name | title                  | salary | tag  |
+------------+-----------+------------------------+--------+------+
| Melinda    | Clifford  | Project Manager        |   8500 | high |
| Harley     | Gilbert   | Software Architect     |   8000 | high |
| Taylor     | Edward    | Software Architect     |   7200 | high |
| Harry      | Clifford  | Database Administrator |   6800 | low  |
| Jack       | Chan      | Test Engineer          |   6500 | low  |
| Vivian     | Dickens   | Database Administrator |   6000 | low  |
| Robin      | Jackman   | Software Engineer      |   5500 | low  |
| Nancy      | Newman    | Software Engineer      |   5100 | low  |
| Eliza      | Clifford  | Software Engineer      |   4750 | low  |
+------------+-----------+------------------------+--------+------+
```



