# SQL For Idiots

Exactly what it sounds like. SQL notes for people (like me) who just can't seem to memorize the commands. We'll try to keep commands here ordered from simple to complex. 

## Section 1: Basic Basics (Create and delete databases and tables, insert records)

**Show what databases are available to work with**

```
SHOW DATABASES;
```

**Create a database**

```
CREATE DATABASE big_company;
```

**Select a database**

```
USE big_company;
```

**Show tables in the database**

```
SHOW TABLES;
```

**Create a new table**

```
CREATE TABLE employees (
    employee_id INT,
    name VARCHAR(80),
    role VARCHAR(80)
);
```

**Describe a table (list its fields and datatypes)**

```
DESC employees;
```

**Show the contents of a table**

```
SELECT * FROM employees;
```

**Delete a table**

```
DROP TABLE employees;
```

**Insert a new record into a table**

```
INSERT INTO employees (employee_id, name, role) 
VALUES (0, 'Jeremy', 'Founder');
```

**(*Shortcut*) insert a new record into a table, where all fields are specified**

```
INSERT INTO employees VALUES (0, 'Jeremy', 'Founder');
```

**Insert mutiple new records into a table**

```
INSERT INTO employees (employee_id, name, role) 
VALUES 
    (1, 'Erica', 'Co-Founder'),
    (2, 'James', 'CFO'),
    (3, 'Leslie', 'CTO');
```

**Create a table with *required* fields (meaning fields which cannot be `NULL`**

```
CREATE TABLE students (
    name VARCHAR(80) NOT NULL,
    gpa INT NOT NULL
);
```

**Create a table with *required* fields and *default* values for those fields**

```
CREATE TABLE students (
    name VARCHAR(80) NOT NULL DEFAULT 'noname',
    gpa INT NOT NULL DEFAULT 0
);
```

**Insert an empty record (defaults will get filled in)**

```
INSERT INTO students () VALUES ();
```

**Insert a record where only some fields are specified**

```
INSERT INTO students (name) VALUES ('James');
```

**Create a table with a primary key**

```
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    team_id INT NOT NULL
);
```

**Create a table with a primary key that increments on its own**

```
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    team_id INT NOT NULL
);
```

**Insert records into a table with a primary key (identical-looking records can still be differentiated using the primary key)**

```
INSERT INTO employees (name, team_id) 
VALUES 
    ('Bob', 25),
    ('Bob', 25),
    ('Bob', 25);
```

**(*Optional*) another way to create a primary key which auto-increments**

```
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    team_id INT NOT NULL,
    PRIMARY KEY(employee_id)
);
```

## Section 2: Working with data (CRUD operations)

**CRUD = Create, Read, Update, Delete**

### Create

**Create a database**

```
CREATE DATABASE big_company;
```

**Create a table**

```
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    team_id INT NOT NULL,
    PRIMARY KEY(employee_id)
);
```

**Create a record in a table**

```
INSERT INTO employees (name, team_id) VALUES ('Bob', 25);
```

### Read

**Select all items from a table (*read*)**

```
SELECT * FROM employees;
```

**Select specific columns**

```
SELECT name FROM employees;
```

**Select records that meet a certain condition**

```
SELECT * FROM employees WHERE name = 'Bob';
```

*Note:* Just because we are using `WHERE` with a specific column, doesn't mean we have to `SELECT` that column. For instance, if I wanted to know which teams had an employee named "Bob", I could do this:

```
SELECT team_id FROM employees WHERE name = 'Bob' ;
```
*Note:* By default, string comparisons are *case insensitive* in MySQL. 

**Select records where one column's value matches the value of another column**

```
SELECT * FROM employees where team_id = employee_id;
```

**Rename one or more columns using `AS`**

```
SELECT employee_id AS id, name FROM employees; 
```

### Update

**Update an existing row in a table**

```
UPDATE employees SET name = 'Other Bob' WHERE employee_id = 1;
```

**Update a single column for all rows at once**

```
UPDATE employees SET name = 'Whatever';
```

**Update multiple columns for all rows at once**

```
UPDATE employees SET name = 'Whatever', team_id = 0;
```

**Delete one row**

```
DELETE FROM employees WHERE employee_id = 1;
```

**Delete one or more rows that match a pattern**

```
DELETE FROM employees WHERE name = 'Whatever';
```

**Delete *all* rows**

```
DELETE FROM employees;
```