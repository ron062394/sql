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
%sql sqlite:///sql-crud.db
```

## **Create Table**
``` python
%%sql
CREATE TABLE IF NOT EXISTS employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    department VARCHAR(50),
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


## **Altering Table**
### Add column
``` python
%%sql ALTER TABLE employees
ADD hire_date DATE;
```
``` python
%%sql
ALTER TABLE employees
ADD performance_rating INT;
```
### Rename column
``` python
%%sql ALTER TABLE employees
RENAME COLUMN hire_date TO hired_date;
```
### DELETE column
``` python
%%sql ALTER TABLE employees
DROP COLUMN hire_date;
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
SET salary = 55000.00
WHERE employee_id = 1;
```
### **multiple column**
``` python
%%sql
UPDATE employees
SET salary = 55.00,
    hire_date = '2024-01-01'
WHERE employee_id = 1;
```
### **Multiple row**
``` python
%%sql
UPDATE employees
SET salary = 66000,
    hire_date = '2024-12-01'
WHERE department = 'Operations';
```

## **Deleting Data**
``` python

```



