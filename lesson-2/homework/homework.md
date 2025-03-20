-- 1. Create Employees table
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    Name VARCHAR(50),
    Salary DECIMAL(10,2)
);

-- 2. Insert records using different approaches
-- Single-row insert
INSERT INTO Employees (EmpID, Name, Salary) VALUES (1, 'John Doe', 5000.00);

-- Multiple-row insert
INSERT INTO Employees (EmpID, Name, Salary) 
VALUES 
    (2, 'Jane Smith', 6000.00),
    (3, 'Alice Brown', 5500.00);

-- 3. Update Salary where EmpID = 1
UPDATE Employees 
SET Salary = 5200.00 
WHERE EmpID = 1;

-- 4. Delete a record where EmpID = 2
DELETE FROM Employees WHERE EmpID = 2;

-- 5. Demonstrate DELETE, TRUNCATE, and DROP commands
-- Create a test table
CREATE TABLE TestTable (
    ID INT PRIMARY KEY,
    Name VARCHAR(50)
);

INSERT INTO TestTable (ID, Name) VALUES (1, 'Test1'), (2, 'Test2');

-- DELETE removes specific records but keeps table structure
DELETE FROM TestTable WHERE ID = 1;

-- TRUNCATE removes all records but keeps table structure
TRUNCATE TABLE TestTable;

-- DROP removes the entire table including its structure
DROP TABLE TestTable;

-- 6. Modify Name column to VARCHAR(100)
ALTER TABLE Employees 
ALTER COLUMN Name VARCHAR(100);

-- 7. Add a new column Department
ALTER TABLE Employees 
ADD Department VARCHAR(50);

-- 8. Change Salary column data type to FLOAT
ALTER TABLE Employees 
ALTER COLUMN Salary FLOAT;

-- 9. Create Departments table
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(50)
);

-- 10. Remove all records from Employees without deleting its structure
TRUNCATE TABLE Employees;


-- Insert five records into the Departments table using INSERT INTO SELECT
INSERT INTO Departments (DepartmentID, DepartmentName)
SELECT DISTINCT TOP 5 EmpID, Department FROM Employees WHERE Department IS NOT NULL;

-- Update the Department of all employees where Salary > 5000 to 'Management'
UPDATE Employees 
SET Department = 'Management' 
WHERE Salary > 5000;

-- Remove all employees but keep the table structure intact
TRUNCATE TABLE Employees;

-- Drop the Department column from the Employees table
ALTER TABLE Employees 
DROP COLUMN Department;

-- Rename the Employees table to StaffMembers
EXEC sp_rename 'Employees', 'StaffMembers';

-- Completely remove the Departments table from the database
DROP TABLE Departments;
