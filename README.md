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

Each data type serves a specific purpose, ensuring data is stored efficiently and operations are performed correctly. Let me know if you'd like more details or examples!
