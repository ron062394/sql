## **Install `SQLite3` Editor Extension**
``` md
`SQLite3 Editor`
```

## **Install `ipython-sql` Package**
``` python
%pip install ipython-sql
```

## **Load the SQL Extension**
``` python
%load_ext sql
```

---
---


## **Create SQLite Database**
``` python
%sql sqlite:///abc-corp.db
```

## **Create Table**
``` python
%%sql
CREATE TABLE IF NOT EXISTS employees (
    employee_id INTEGER PRIMARY KEY AUTOINCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    department VARCHAR(50) NOT NULL,
    salary DECIMAL(10, 2) NOT NULL    
);
```

## **Auto Increament**
```
%%sql
CREATE TABLE IF NOT EXISTS employees (
    employee_id INTEGER PRIMARY KEY AUTOINCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    department VARCHAR(50) NOT NULL,
    salary DECIMAL(10, 2) NOT NULL    
);
```



## **Other Data Types**
``` md	
    ### id INT PRIMARY KEY,
    - Description: Represents whole numbers without fractional components.
    - Usage: Suitable for storing counts, IDs, or other whole number data.

    ### decimal_column DECIMAL(10, 2),
    - Represents fixed-point numbers with a specified precision (total digits) and scale (digits to the right of the decimal point).
    - Usage: Ideal for financial data or where precise calculations with fixed decimal places are required.

    ### char_column CHAR(10),
    - Description: Fixed-length character strings
    - Usage: Suitable for fields where data length is consistent, such as postal codes or fixed-format identifiers.

    ### varchar_column VARCHAR(255),
    - Description: Variable-length character strings.
    - Usage: Commonly used for text fields with varying lengths, such as names, addresses, or descriptions.
    
    ### text_column TEXT,
    - Description: Variable-length character strings with no specified maximum length.
    - Usage: Used for large blocks of text where the exact length is unpredictable, such as comments or lengthy descriptions.
    
    ### boolean_column BOOLEAN
    - Description: Stores boolean values (TRUE or FALSE).
    - Usage: Used for fields that represent binary states or conditions, such as status indicators (active, inactive), flags, or logical condition
```


## **Check if the employee table is created successfully**
``` python
%sql SELECT name FROM sqlite_master WHERE type='table';
```

## **Check the structure of the table**
``` python
%sql PRAGMA table_info('employees');
```


## **Altering Table**
### Add column
``` python
%%sql ALTER TABLE employees
ADD hiring_date DATE;

ALTER TABLE employees
ADD performance_rating INT;

ALTER TABLE employees
ADD birth_date DATE;
```
### Rename column
``` python
%%sql ALTER TABLE employees
RENAME COLUMN hiring_date TO hire_date;
```
### DELETE column
``` python
%%sql ALTER TABLE employees
DROP COLUMN birth_date;
```


## **Deleting a Table**
``` python
%sql DROP TABLE employees;
```

## **Inserting Data**
``` python
%%sql
INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date, performance_rating)
VALUES (1, 'John', 'Doe', 'Sales', 50000.00, '2024-04-23', 3);

INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date, performance_rating)
VALUES (2, 'Jane', 'Smith', 'Marketing', 55000.00, '2024-04-25', 4);

INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date, performance_rating)
VALUES (3, 'Michael', 'Johnson', 'Sales', 60000.00, '2024-04-26', 5);

INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date, performance_rating)
VALUES (4, 'Emily', 'Davis', 'Operations', 62000.00, '2024-04-27', 2);

INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date, performance_rating)
VALUES (5, 'David', 'Wilson', 'Operations', 58000.00, '2024-04-28', 1);
```

## **Selecting Data**
``` python
%sql SELECT * FROM employees;
```


## **Selecting Specific Columns**
``` python
%%sql SELECT first_name, last_name, department
FROM employees;
```



## **Updating Data**
### **Single column**
``` python
%%sql UPDATE employees
SET salary = 55.00
WHERE employee_id = 1;
```
### **multiple column**
``` python
%%sql
UPDATE employees
SET salary = 555.00,
    hired_date = '2024-02-01'
WHERE employee_id = 1;
```
### **Multiple row**
``` python
%%sql
UPDATE employees
SET salary = 66000,
    hired_date = '2024-12-01'
WHERE department = 'Operations';
```

## **Deleting Data**
``` python
%%sql DELETE FROM employees
WHERE employee_id = 1;
```

## **Deleting Table**
``` python
#%sql DROP TABLE employees;
```


## **Notes**
## **Dates and Time**
- DATE: Date (e.g., YYYY-MM-DD).
- TIME: Time of day (e.g., HH:MM:SS).
- TIMESTAMP/DATETIME: Date and time combined (e.g., YYYY-MM-DD HH:MM:SS).
``` python
-- Creating a table with date/time types
CREATE TABLE date_time_types (
    id INT PRIMARY KEY,
    date_column DATE,
    time_column TIME,
    timestamp_column TIMESTAMP
);
```
``` python
-- Inserting sample data into date_time_types
INSERT INTO date_time_types (id, date_column, time_column, timestamp_column)
VALUES 
    (1, '2024-07-01', '12:30:00', '2024-07-01 12:30:00'),
    (2, '2024-07-02', '15:45:00', '2024-07-02 15:45:00'),
    (3, '2024-07-03', '09:00:00', '2024-07-03 09:00:00');
```



