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

If you have specific queries about any DDL command, feel free to ask!
