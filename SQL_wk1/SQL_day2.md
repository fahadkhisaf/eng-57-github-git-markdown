# SQL day 2

# composite key vs candidate key  

The main difference between candidate key and composite key is that candidate key is a super key with no redundant attributes while the composite key is a key with two or many attributes to identify the rows of the table.

# Normal forms
- 1ST  NORMAL FORM: Make everything atomic, One piece of data per cell, there should be no repeating keys

- 2ND NORMAL FORM: A database is in second normal form when its in 1ST NF and all the non-key attributes are fully functional dependent on the primary key

- 3RD NORMAL FORM: it is in 2ND NF, There is no transitive function depenency

# Revision questions
Q1)
- Create two tables each having primary keys: person, employees
-  Create foreign key in one table referencing the primary key in the other table
-  ON DELETE CASADE which if you apply to a primary key will automatically delete that data from the foeign keys.

```SQL
CREATE TABLE employees(
    employee_id VARCHAR(6),
    employee_city VARCHAR(3),
    employee_type VARCHAR(4),

    PRIMARY KEY (employee_id)
)

CREATE TABLE redudancy_list(
    employee_id VARCHAR(5),
    employee_salary VARCHAR(5),
    employee_behaviour CHAR(1),

    PRIMARY KEY (employee_salary),
    FOREIGN KEY(employee_city) REFERENCES employees
)
```
# SQL fundamentals
- * = means to select all columns
- Only after 'AS' operator use double quotes
- WHERE = is used to filter the data eg:
```SQL
SELECT * FROM Employees
WHERE city = 'London'
```

- EXAMPLE: How many products are discontinued?
```SQL
SELECT COUNT (Discontinued) AS 'Number of prodcuts discontinued'
FROM Prodcuts
WHERE Discontinued !=0
```
# QUERIES
 ```SQL
 1)
SELECT CompanyName,City,Country,Region
FROM Customers WHERE Region='BC'

2)
SELECT TOP 100 CompanyName, City FROM Customers
WHERE Country='France'

3)
SELECT ProductName,Unitprice FROM Products
WHERE CategoryID=1 AND Discontinued='0'

4)
SELECT ProductName, UnitPrice FROM Products
WHERE UnitsInStock >0 OR UnitPrice>29.99

5)
SELECT DISTINCT Country FROM Customers
WHERE ContactTitle = 'Owner'

6)
SELECT DISTINCT Country
FROM Customers
WHERE ContactTitle='Owner' AND Country LIKE '___i%'

# comment three underscores means the thrid letter must be i

7)
SELECT ProductName
FROM Products WHERE ProductName LIKE 'ch%'

8)
SELECT*
FROM Customers WHERE Region LIKE '_A'
#To find regions ending in A

9)
SELECT*
FROM Customers WHERE Region IN ('WA','SP')
# if we need to find customers in two specific named regions

10)
SELECT*
FROM EmployeeTerritories
WHERE TerritoryID BETWEEN 06800 AND 09999
# if we need to find territories in a range of IDS

11)
q) What are the names and productIDs of the products with a unit price below 5.00?

SELECT * FROM Categories
WHERE CategoryName LIKE '[BS]%'

q2) How many orders are there for EmployeeIDS 5 and 7 (the total for both)

SELECT COUNT (*) AS 'Number of orders'
FROM Orders
WHERE EmployeeID IN (5,7)

12)
SELECT CompanyName AS 'Company Name',
City +','+ Country AS 'City'
FROM Customers

13) In order to filter based on NULLs simply use is NULL or IS NOT NULLs
 
