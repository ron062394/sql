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
