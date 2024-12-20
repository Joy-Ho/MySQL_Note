# MySQL Note_3
Relationship

> Two tables, **customers** and **orders**, **id**  and **customer_id** are the same columns
```bash 
source C:\Users\admin\Documents\customer_order.sql
```

```bash
Result:

select * from customers;
+----+------------+-----------+----------------+
| id | first_name | last_name | email          |
+----+------------+-----------+----------------+
|  1 | Robin      | Jackman   | roj@gmail.com  |
|  2 | Taylor     | Edward    | taed@gmail.com |
|  3 | Vivian     | Dickens   | vidi@gmail.com |
|  4 | Harley     | Gilbert   | hgi@gmail.com  |
|  5 | A          | B         | ab@gmail.com   |
+----+------------+-----------+----------------+
select * from orders;
+----+------------+--------+-------------+
| id | order_date | amount | customer_id |
+----+------------+--------+-------------+
|  1 | 2001-10-12 |  99.12 |           1 |
|  2 | 2001-09-21 | 110.99 |           2 |
|  3 | 2001-10-13 |  12.19 |           1 |
|  4 | 2001-11-29 |  88.09 |           3 |
|  5 | 2001-11-11 | 205.01 |           4 |
+----+------------+--------+-------------+
```

#

> use ID from **customers** table to extract the customer's order_date and amount from **orders** table.
> Extract Robin Jackman's order_date and amount
```bash 
 select * from orders where customer_id = (select id from customers where first_name="Robin" and last_name="Jackman");
```

```bash
Result:
+----+------------+--------+-------------+
| id | order_date | amount | customer_id |
+----+------------+--------+-------------+
|  1 | 2001-10-12 |  99.12 |           1 |
|  3 | 2001-10-13 |  12.19 |           1 |
+----+------------+--------+-------------+
```

#

> FOREIGN KEY, If ID = 3 does not in **customer** table, **orders** table cannot insert the record of ID = 3.
```bash 
CREATE TABLE orders(
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_date DATE,
    amount DECIMAL(8,2),
    customer_id INT,
    FOREIGN KEY(customer_id) REFERENCES customers(id)
);
```

```bash
Result:
The Key of customer_id is MUL.
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| id          | int          | NO   | PRI | NULL    | auto_increment |
| order_date  | date         | YES  |     | NULL    |                |
| amount      | decimal(8,2) | YES  |     | NULL    |                |
| customer_id | int          | YES  | MUL | NULL    |                |
+-------------+--------------+------+-----+---------+----------------+
```

> ID = 10 is not in **customer** table, fail to insert record of ID = 10 in **orders** table
```bash 

Result:
INSERT INTO order(order_date, amount, customer_id) VALUES("2024-12-10", 327, 10);

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'order(order_date, amount, customer_id) VALUES("2024-12-10", 327, 10)' at line 1
```

#

> **INNER JOIN**, select records that include in both table. Do not include the record that first_name=A, last_name=B
```bash 
 select * from customers inner join orders where customers.id=orders.customer_id;
```

```bash
Result:
+----+------------+-----------+----------------+----+------------+--------+-------------+
| id | first_name | last_name | email          | id | order_date | amount | customer_id |
+----+------------+-----------+----------------+----+------------+--------+-------------+
|  1 | Robin      | Jackman   | roj@gmail.com  |  1 | 2001-10-12 |  99.12 |           1 |
|  1 | Robin      | Jackman   | roj@gmail.com  |  3 | 2001-10-13 |  12.19 |           1 |
|  2 | Taylor     | Edward    | taed@gmail.com |  2 | 2001-09-21 | 110.99 |           2 |
|  3 | Vivian     | Dickens   | vidi@gmail.com |  4 | 2001-11-29 |  88.09 |           3 |
|  4 | Harley     | Gilbert   | hgi@gmail.com  |  5 | 2001-11-11 | 205.01 |           4 |
+----+------------+-----------+----------------+----+------------+--------+-------------+
```

#
> **LEFT JOIN**, from A left join on B => based on A, return all records from A and match B.

> Extract the total account of all customers
```bash 
SELECT first_name, last_name, SUM(amount) from customers left join orders on customers.id=orders.customer_id group by customers.id;
```

```bash
Result:
+------------+-----------+-------------+
| first_name | last_name | SUM(amount) |
+------------+-----------+-------------+
| Robin      | Jackman   |      111.31 |
| Taylor     | Edward    |      110.99 |
| Vivian     | Dickens   |       88.09 |
| Harley     | Gilbert   |      205.01 |
| A          | B         |        NULL |
+------------+-----------+-------------+
```

> If the customers do not purchases, the amount shows NULL. Change NULL to 0, and order based on amount
```bash 
SELECT first_name, last_name, IFNULL(SUM(amount), 0) total_amount from customers left join orders on customers.id=orders.customer_id group by customers.id order by total_amount desc;
```

```bash
Result:
+------------+-----------+--------------+
| first_name | last_name | total_amount |
+------------+-----------+--------------+
| Harley     | Gilbert   |       205.01 |
| Robin      | Jackman   |       111.31 |
| Taylor     | Edward    |       110.99 |
| Vivian     | Dickens   |        88.09 |
| A          | B         |         0.00 |
+------------+-----------+--------------+
```

#
> **Right JOIN**, from A right join on B => based on B, return all records from B and match A. 
```bash 
select * from customers right join orders on customers.id=orders.customer_id
```

```bash
Result:
Do not include the record that first_name=A, last_name=B

+------+------------+-----------+----------------+----+------------+--------+-------------+
| id   | first_name | last_name | email          | id | order_date | amount | customer_id |
+------+------------+-----------+----------------+----+------------+--------+-------------+
|    1 | Robin      | Jackman   | roj@gmail.com  |  1 | 2001-10-12 |  99.12 |           1 |
|    2 | Taylor     | Edward    | taed@gmail.com |  2 | 2001-09-21 | 110.99 |           2 |
|    1 | Robin      | Jackman   | roj@gmail.com  |  3 | 2001-10-13 |  12.19 |           1 |
|    3 | Vivian     | Dickens   | vidi@gmail.com |  4 | 2001-11-29 |  88.09 |           3 |
|    4 | Harley     | Gilbert   | hgi@gmail.com  |  5 | 2001-11-11 | 205.01 |           4 |
+------+------------+-----------+----------------+----+------------+--------+-------------+
```

