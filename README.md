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

