# sql

# Basics
USE sql_store;
SELECT *
FROM customers
WHERE state = 'CA'
ORDER BY first_name
LIMIT 3;
* SQL is not a case-senistive language
* In MYSQL every statement must be terminated with a semicolon.


# SELECT Clause
SELECT (points * 10 + 20) AS discount_factor
FROM customers
Order of operations
* Paranthesis
* Multiplication/division
* Addition/ Subtraction

# WHERE Clause
We use the WHERE clause to filter data

Comparison operators:
* Greater than:>
* Greater than or equal to: >=
* Less than <
* Less than or equal to: <=
* Equal: =
* Not equal: <>
* Not equal: !=

# Logical Operators
SELECT *
FROM customers
WHERE birthdate > '1990-01-01' AND points>1000

SELECT *
FROM customers
WHERE birthdate > '1990-01-01' OR points>1000

SELECT *
FROM customers
WHERE NOT (birthdate > '1990-01-01')

# IN Operator
SELECT *
FROM customers
WHERE state IN('VA','NY','CA')

# BETWEEN operator
SELECT *
FROM customers
WHERE points between 100 AND 200

# LIKE Operator
SELECT *
FROM customers
WHERE first_name LIKE 'b%'
 * %: any number of characters
 * _: exactly one character

# REGEXP Operator
SELECT *
FROM customers
WHERE first_name REGEXP '^a'

* ^: begining of string
* $: end of string
* |: logical OR
* [abc]: match any single characters
* [a-d]: any characters from a to d

WHERE first_name REGEXP 'ey$|on$' --> first name ends with EY or ON
WHERE first_name REGEXP '^my|se' --> first name starts with NY or contains SE
WHERE first_name REGEXP 'b[ru]'  

# IS NULL Operator
SELECT *
FROM customers
 WHERE phone IS NULL 

# ORDER BY CLAUSE
SELECT *
FROM customers
ORDER BY state, first_name DESC  -->STATE in ascending order and first_name in descending order

# LIMIT CLAUSE
SELECT *
FROM customers
LIMIT 3
Skip 6 customers and return 3

SELECT *
FROM customers
LIMIT 6, 3

# INNER Joins
SELECT *
 FROM customers c
 JOIN orders o
   ON c.customer_id = o.customer_id
   
# OUTER JOINS
 SELECT *
 FROM customers c
  LEFT JOIN orders o
    ON c.customer_id = o.customer_id  --> Returns all customers whether they have any orders or not
    
# USING CLAUSE
If the column names are exactly same, we can simplify the join with the USING clause
SELECT *
FROM customers c
 JOIN orders o
   USING (customers_id)
   
# CROSS JOINS
Combine every color with every size

SELECT *
FROM colors
 CROSS JOIN sizes

# Unions 
 Combine records from multiple result sets
 
SELECT name, address
 FROM customers
 UNION
 SELECT name, address
 FROM clients

# Inserting Data
 Insert a single record
 
INSERT INTO customers(first_name, phone, points)
VALUES ('RONAK', NULL, DEFAULT)

INSERT INTO customers(first_name, phone, points)
VALUES
('RONAK', NULL, DEFAULT),
('AKASH','1234', 10)
