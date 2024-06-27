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
``` python
%%sql
CREATE TABLE sample_table (
    -- Numeric types
    id INT PRIMARY KEY,
    integer_column INT,
    decimal_column DECIMAL(10, 2),
    
    -- Character/String types
    char_column CHAR(10),
    varchar_column VARCHAR(255),
    text_column TEXT,
    
    -- Time types
    time_column TIME,
    timestamp_column TIMESTAMP,
    
    -- Boolean type
    boolean_column BOOLEAN
);

INSERT INTO sample_table (id, integer_column, decimal_column,
                          char_column, varchar_column, text_column,
                          time_column, timestamp_column,
                          boolean_column)
VALUES (1, 123, 45.67,
        'ABC', 'Sample Text', 'Lorem ipsum dolor sit amet.',
        '10:00:00', '2024-06-30 10:00:00',
        TRUE),
       (2, 456, 89.01,
        'XYZ', 'Another Text', 'Nulla vitae elit libero.',
        '15:30:00', '2024-07-01 15:30:00',
        FALSE);
```
