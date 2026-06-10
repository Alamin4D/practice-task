# Book Store Database Management System

## Project Overview

This project demonstrates a simple Book Store Database Management System using SQL. The database stores information about customers, books, and orders placed by customers. It also includes various SQL queries to perform data retrieval, aggregation, filtering, and table modification operations.

---

## Database Structure

### 1. Customers Table

Stores customer information.

| Column Name         | Data Type    | Description         |
| ------------------- | ------------ | ------------------- |
| customer_id         | INT          | Primary Key         |
| customer_first_name | VARCHAR(50)  | Customer First Name |
| last_name           | VARCHAR(50)  | Customer Last Name  |
| email               | VARCHAR(100) | Customer Email      |
| city                | VARCHAR(50)  | Customer City       |
| country             | VARCHAR(50)  | Customer Country    |
| registration_date   | DATE         | Registration Date   |

---

### 2. Books Table

Stores book information.

| Column Name      | Data Type     | Description      |
| ---------------- | ------------- | ---------------- |
| book_id          | INT           | Primary Key      |
| title            | VARCHAR(200)  | Book Title       |
| author           | VARCHAR(100)  | Author Name      |
| genre            | VARCHAR(50)   | Book Genre       |
| price            | DECIMAL(10,2) | Book Price       |
| publication_year | INT           | Publication Year |
| stock_quantity   | INT           | Available Stock  |

---

### 3. Orders Table

Stores customer orders.

| Column Name  | Data Type     | Description             |
| ------------ | ------------- | ----------------------- |
| order_id     | INT           | Primary Key             |
| customer_id  | INT           | Foreign Key (Customers) |
| book_id      | INT           | Foreign Key (Books)     |
| order_date   | DATE          | Order Date              |
| quantity     | INT           | Quantity Purchased      |
| total_amount | DECIMAL(10,2) | Total Order Value       |

---

## Relationships

* One customer can place multiple orders.
* One book can appear in multiple orders.
* `customer_id` in the Orders table references the Customers table.
* `book_id` in the Orders table references the Books table.

---

## Sample SQL Operations

### Display Books Ordered by Price

```sql
SELECT title, price
FROM books
ORDER BY price ASC;
```

### Find Distinct Customer Countries

```sql
SELECT DISTINCT country
FROM customers;
```

### Find Books Starting with "The"

```sql
SELECT *
FROM books
WHERE title LIKE 'The%';
```

### Find Fantasy Books

```sql
SELECT *
FROM books
WHERE genre = 'Fantasy';
```

### Count Total Orders

```sql
SELECT COUNT(*) AS total_orders
FROM orders;
```

### Average Book Price by Genre

```sql
SELECT genre, AVG(price) AS average_price
FROM books
GROUP BY genre
HAVING AVG(price) > 14;
```

### Customers from USA or UK with .com Emails

```sql
SELECT *
FROM customers
WHERE email LIKE '%.com'
AND (country = 'USA' OR country = 'UK');
```

### Customer Full Name in Uppercase

```sql
SELECT
UPPER(customer_first_name || ' ' || last_name) AS full_name,
email,
LOWER(city) AS city
FROM customers
WHERE country IN ('USA','UK');
```

### Revenue Analysis for June 2023

```sql
SELECT
SUM(total_amount) AS total_revenue,
AVG(total_amount) AS average_order_amount,
MAX(total_amount) AS maximum_order_amount,
MIN(total_amount) AS minimum_order_amount
FROM orders
WHERE order_date BETWEEN '2023-06-01' AND '2023-06-30';
```

---

## Table Modification

Rename column:

```sql
ALTER TABLE customers
RENAME COLUMN first_name TO customer_first_name;
```

---

## Key SQL Concepts Used

* CREATE TABLE
* PRIMARY KEY
* FOREIGN KEY
* INSERT INTO
* SELECT
* WHERE
* LIKE
* DISTINCT
* ORDER BY
* COUNT()
* AVG()
* SUM()
* MAX()
* MIN()
* GROUP BY
* HAVING
* ALTER TABLE
* RENAME COLUMN

---

## Technologies Used

* PostgreSQL
* SQL

---

## Author

Alamin Hossain
MERN Stack Developer
