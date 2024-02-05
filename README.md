# SQL For Idiots

Exactly what it sounds like. SQL notes for people (like me) who just can't seem to memorize the commands. We'll try to keep commands here ordered from simple to complex. 

**Shoe what databases are available to work with**

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

**Describe a table (list its fields and datat types)**

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

