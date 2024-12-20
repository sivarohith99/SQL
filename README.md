DDL stands for **Data Definition Language** in **DBMS (Database Management System)**. It consists of commands used to define or modify the structure of database objects such as tables, indexes, and schemas.

### Common DDL Commands

1. **CREATE**: Used to create new database objects like tables, views, or schemas.
   ```sql
   CREATE TABLE Employees (
       EmployeeID INT PRIMARY KEY,
       Name VARCHAR(50),
       Age INT,
       Department VARCHAR(50)
   );
   ```

2. **ALTER**: Used to modify the structure of existing database objects.
   - Add a new column:
     ```sql
     ALTER TABLE Employees ADD Salary DECIMAL(10, 2);
     ```
   - Modify a column:
     ```sql
     ALTER TABLE Employees MODIFY Name VARCHAR(100);
     ```
   - Drop a column:
     ```sql
     ALTER TABLE Employees DROP COLUMN Age;
     ```

3. **DROP**: Used to delete database objects permanently.
   ```sql
   DROP TABLE Employees;
   ```

4. **TRUNCATE**: Used to delete all rows from a table but keep the structure intact.
   ```sql
   TRUNCATE TABLE Employees;
   ```

5. **RENAME**: Used to rename database objects.
   ```sql
   RENAME TABLE Employees TO Staff;
   ```

6. **COMMENT**: Used to add comments to database objects for documentation.
   ```sql
   COMMENT ON TABLE Employees IS 'Table storing employee details';
   ```

---

### Key Characteristics of DDL
- **Structure-Oriented**: DDL commands deal with the schema and structure of the database.
- **Autocommit**: Changes made using DDL commands are automatically committed to the database and cannot be rolled back.
- **Non-Data Handling**: DDL focuses on defining and managing structures; it does not deal with the actual data inside the tables.

A **Data Type** in SQL specifies the type of data that a column in a table can hold. It ensures data consistency and defines how data is stored, retrieved, and processed in a database.

### Categories of SQL Data Types

#### 1. **Numeric Data Types**
   - Used to store numeric values, both integers and floating-point numbers.
   - **Examples**:
     - `INT` or `INTEGER`: Stores whole numbers.
       ```sql
       Salary INT;
       ```
     - `SMALLINT`: Stores smaller range of integers.
     - `BIGINT`: Stores larger range of integers.
     - `DECIMAL(p, s)` or `NUMERIC(p, s)`: Stores fixed-point numbers with precision `p` and scale `s`.
       ```sql
       Price DECIMAL(10, 2); -- Max 10 digits, 2 after decimal
       ```
     - `FLOAT` or `REAL`: Stores floating-point numbers.
       ```sql
       Rating FLOAT(2);
       ```

#### 2. **Character/String Data Types**
   - Used to store text or string data.
   - **Examples**:
     - `CHAR(n)`: Fixed-length string of size `n`.
       ```sql
       Country CHAR(2); -- Always stores 2 characters
       ```
     - `VARCHAR(n)`: Variable-length string with a maximum size of `n`.
       ```sql
       Name VARCHAR(50);
       ```
     - `TEXT`: Large text data (size may vary depending on the database system).

#### 3. **Date and Time Data Types**
   - Used to store date and time values.
   - **Examples**:
     - `DATE`: Stores dates (e.g., `YYYY-MM-DD`).
       ```sql
       BirthDate DATE;
       ```
     - `TIME`: Stores time (e.g., `HH:MI:SS`).
       ```sql
       MeetingTime TIME;
       ```
     - `DATETIME`: Stores both date and time.
       ```sql
       OrderDate DATETIME;
       ```
     - `TIMESTAMP`: Stores date and time with time zone information.
     - `YEAR`: Stores year values (e.g., `YYYY`).

#### 4. **Boolean Data Type**
   - Used to store `TRUE`, `FALSE`, or `NULL`.
   - Some databases use `BIT` or `TINYINT(1)` for boolean values.

#### 5. **Binary Data Types**
   - Used to store binary data such as images, files, or encrypted data.
   - **Examples**:
     - `BINARY(n)`: Fixed-length binary data.
     - `VARBINARY(n)`: Variable-length binary data.
     - `BLOB`: Binary Large Objects.

#### 6. **Spatial Data Types** (Specific to some databases)
   - Used to store geometric or geographic data.
   - **Examples**:
     - `POINT`, `LINESTRING`, `POLYGON`.

#### 7. **Other Data Types**
   - `JSON`: Stores JSON-formatted text.
   - `XML`: Stores XML data.
   - `ENUM`: Stores predefined values (specific to MySQL).
     ```sql
     Status ENUM('Active', 'Inactive');
     ```
   - `SET`: Stores multiple predefined values (specific to MySQL).

---

### Example Usage
```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50),
    JoiningDate DATE,
    Salary DECIMAL(10, 2),
    IsActive BOOLEAN
);
```

Each data type serves a specific purpose, ensuring data is stored efficiently and operations are performed correctly. 

**Constraints** in SQL are rules enforced on data in tables to ensure data integrity, accuracy, and reliability. They define conditions that data in a database must satisfy.

---

### Types of SQL Constraints

#### 1. **NOT NULL**
   - Ensures that a column cannot have a `NULL` value.
   - **Example**:
     ```sql
     CREATE TABLE Employees (
         EmployeeID INT NOT NULL,
         Name VARCHAR(50) NOT NULL
     );
     ```

#### 2. **UNIQUE**
   - Ensures that all values in a column (or a combination of columns) are unique.
   - **Example**:
     ```sql
     CREATE TABLE Employees (
         Email VARCHAR(100) UNIQUE
     );
     ```
   - **Note**: Multiple `UNIQUE` constraints can be applied in a table.

#### 3. **PRIMARY KEY**
   - Combines the `NOT NULL` and `UNIQUE` constraints. It uniquely identifies each row in a table.
   - A table can have only one `PRIMARY KEY`.
   - **Example**:
     ```sql
     CREATE TABLE Employees (
         EmployeeID INT PRIMARY KEY,
         Name VARCHAR(50)
     );
     ```

#### 4. **FOREIGN KEY**
   - Establishes a relationship between two tables by linking a column (or a set of columns) in one table to the `PRIMARY KEY` in another.
   - **Example**:
     ```sql
     CREATE TABLE Departments (
         DepartmentID INT PRIMARY KEY,
         DepartmentName VARCHAR(50)
     );

     CREATE TABLE Employees (
         EmployeeID INT PRIMARY KEY,
         DepartmentID INT,
         FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
     );
     ```

#### 5. **CHECK**
   - Ensures that all values in a column satisfy a specific condition.
   - **Example**:
     ```sql
     CREATE TABLE Employees (
         EmployeeID INT PRIMARY KEY,
         Age INT CHECK (Age >= 18),
         Salary DECIMAL(10, 2) CHECK (Salary > 0)
     );
     ```

#### 6. **DEFAULT**
   - Provides a default value for a column when no value is specified.
   - **Example**:
     ```sql
     CREATE TABLE Employees (
         EmployeeID INT PRIMARY KEY,
         IsActive BOOLEAN DEFAULT TRUE
     );
     ```

#### 7. **INDEX (Constraint-Like Behavior)**
   - Creates an index to enhance query performance on columns. It is not technically a constraint but supports unique constraints.
   - **Example**:
     ```sql
     CREATE UNIQUE INDEX idx_email ON Employees(Email);
     ```

---

### Combining Constraints
Multiple constraints can be applied to a single column, except for `PRIMARY KEY` and `UNIQUE`, which cannot overlap directly.
```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    Age INT CHECK (Age > 18),
    IsActive BOOLEAN DEFAULT TRUE
);
```

---

### Modifying Constraints
Constraints can also be added or dropped from existing tables using `ALTER TABLE`:
- **Add a Constraint**:
  ```sql
  ALTER TABLE Employees ADD CONSTRAINT chk_age CHECK (Age >= 18);
  ```
- **Drop a Constraint**:
  ```sql
  ALTER TABLE Employees DROP CONSTRAINT chk_age;
  ```

---

Constraints are crucial for maintaining **data integrity** in relational databases. 

**Data Manipulation Language (DML)** in SQL is used to perform operations on the data stored in database tables. It allows users to retrieve, insert, update, and delete data, focusing on the **manipulation of data**, not the structure of the database.

---

### Key DML Commands

#### 1. **SELECT**
   - Retrieves data from one or more tables or views.
   - **Example**:
     ```sql
     SELECT * FROM Employees;
     ```
   - **Example with conditions**:
     ```sql
     SELECT Name, Salary 
     FROM Employees 
     WHERE Department = 'IT';
     ```

#### 2. **INSERT**
   - Adds new records (rows) to a table.
   - **Example**:
     ```sql
     INSERT INTO Employees (EmployeeID, Name, Age, Department)
     VALUES (1, 'John Doe', 30, 'IT');
     ```
   - Insert data into specific columns:
     ```sql
     INSERT INTO Employees (Name, Department)
     VALUES ('Jane Smith', 'HR');
     ```

#### 3. **UPDATE**
   - Modifies existing records in a table.
   - **Example**:
     ```sql
     UPDATE Employees
     SET Salary = 75000
     WHERE EmployeeID = 1;
     ```
   - Update multiple columns:
     ```sql
     UPDATE Employees
     SET Age = 31, Department = 'Finance'
     WHERE EmployeeID = 1;
     ```

#### 4. **DELETE**
   - Removes records from a table.
   - **Example**:
     ```sql
     DELETE FROM Employees
     WHERE EmployeeID = 1;
     ```
   - Remove all records (without deleting the table):
     ```sql
     DELETE FROM Employees;
     ```

---

### Characteristics of DML
1. **Data-Focused**: DML commands work with the data inside tables, not the table structure.
2. **Transactional**: DML commands can be rolled back or committed. They are part of a database transaction.
   - **ROLLBACK**: Revert changes made by DML commands.
   - **COMMIT**: Save changes made by DML commands.
   ```sql
   BEGIN TRANSACTION;
   INSERT INTO Employees (Name, Department) VALUES ('Alice', 'HR');
   ROLLBACK; -- Changes reverted
   COMMIT;   -- Save changes to the database
   ```

---

### DML vs. DDL
| **Feature**         | **DML**                                    | **DDL**                        |
|----------------------|--------------------------------------------|--------------------------------|
| **Focus**           | Manipulates data in the database           | Defines/modifies database structure |
| **Commands**        | `SELECT`, `INSERT`, `UPDATE`, `DELETE`     | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| **Transactional**   | Yes (can be rolled back or committed)      | No (auto-committed changes)   |

---

DML is essential for interacting with and managing the data in databases. Let me know if you want more examples or details!
