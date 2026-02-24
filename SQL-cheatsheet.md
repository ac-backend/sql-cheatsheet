# PostgreSQL Cheatsheet

Each student will complete the Description and Example sections for the SQL clause assigned to them.

For each clause:

1. In the **Description**, explain what the clause does in plain language.main
2. In the **Example**, write a working SQL statement that shows how the clause is used (like the `SELECT and `CREATE TABLE` examples below).
3. As a reference, `SELECT` and `CREATE TABLE` are already done for you.

---

### 1. `SELECT`

**Description:** `SELECT *` returns all columns from the provided table. You can also do `SELECT column_name_1, column_name_2` to return specific columns from the provided table.

**Example:**

```sql
SELECT *
FROM movies;
```

### 2. `CREATE TABLE`

**Description:** `CREATE TABLE` creates a new table in a database. It allows one to specify the name of the table, the name of each column, and each column's data type in the table.

**Example:**

```sql
CREATE TABLE friends (
  friend_id SERIAL PRIMARY KEY,
  name VARCHAR,
  birthday DATE
);
```

### 3. `INSERT INTO` — assigned to Ainslie

**Description:** `INSERT INTO` adds a new row of information to a table that already exists. You have to write the table name, list the columns you want to fill in, and then write the values you want to add.

**Example:**

```sql
INSERT INTO daughter (name, birthday)
VALUES ('Asia Adams', '2013-06-21');
```

### 4. `UPDATE` — assigned to Babz

**Description:**

**Example:**

```sql
UPDATE friends
SET name = 'Babz'
WHERE friend_id = 1;
```

### 5. `DELETE FROM` — assigned to Haine

**Description:** `DELETE FROM` removes one or more rows from the table. You can use it with a `WHERE` clause to delete specific rows, or without one to delete all rows in the table.

**Example:**

```sql
DELETE FROM friends 
WHERE friend_id = 3;
```

### 6. `GROUP BY` — assigned to Jackie

**Description:** The GROUP BY clause will group records in a result set by identical values in one or more columns. It is often used in combination with aggregate functions to query information of similar records. The GROUP BY clause can come after FROM or WHERE but must come before any ORDER BY or LIMIT clause.

The given query will count the number of movies per rating.



**Example:**

```sql
SELECT rating, 
   COUNT(*) 
FROM movies 
GROUP BY rating;
```

### 7. `ORDER BY` — assigned to Jenny

**Description:** 
The ORDER BY clause in SQL is used to sort the result set of a query in a specific order based on one or more columns. This clause is commonly used to arrange data in ascending or descending order, allowing you to control the presentation of data for better analysis and readability.

**Example:**

```
SELECT *
FROM Customers
ORDER BY country;

```

### 8. `INNER JOIN` — assigned to Megan

**Description:**

**Example:**

```sql

```

### 9. `LIMIT` — assigned to Mimi

**Description:** LIMIT clause is used to control the number of records returned by a query. It helps you retrieve only a specific portion of data instead of the entire result set, which is especially useful when working with large databases.

**Example:**
```sql
SELECT *
FROM employees
WHERE salary > 60000
LIMIT 10

```

### 10. `ON CONFLICT` — assigned to Priscilla

**Description:** `ON CONFLICT` checks for duplicate values. After a conflict is found, if you gave your query instructions as to how to handle the conflict, it will do so.

**Example:**
Lets say that you create a table of countries and `INSERT` the following.
```sql
INSERT INTO country_counts (country_name, count)
VALUES	('Mexico', 1),
		('Cuba', 1),
        ('Brazil', 1),
        ('Ethiopia', 1);
```
This creates a table with both a country and an assigned value into the `count` column. The data type of which, is `INTEGER`.
Then, lets say that you attempt to `INSERT` 'mexico' again.

```sql
INSERT INTO country_counts (country_name, count)
VALUES ('Mexico', 1)
ON CONFLICT (country_name)
DO UPDATE SET count = country_counts.count + 1
RETURNING count;
```
Instead of crashing and returning an error, our `INSERT` will instead see the conflict. In this case, specifically a conflict in our `country_name`. The following line gives the query instructions to follow. In this query, we take the count value and add 1 to the `INTEGER`. Following that, we have the query return the value of `count`.


### 11. `LIKE` — assigned to Stephanie

**Description:** `LIKE` is used in a `WHERE` clause to search for a specific pattern in a column. The % symbol is a wildcard that represents more characters. This example shows all names in the friends table that start with "S".

**Example:**

```sql
SELECT *
FROM friends
WHERE name LIKE 'S%';

```

### 12. `COUNT` — assigned to Tee

**Description:** The COUNT() aggregate function returns the total number of rows that match the specified criteria.

**Example:** For instance, to find the total number of employees who have more than 9 years of experience, the given query can be used.

```sql
SELECT COUNT(*)
FROM employees
WHERE experience > 9;
```
