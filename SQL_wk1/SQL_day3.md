# SQL DAY 3

# BODMAS
- Brackets, Other-indices, Division, Multiplication, Addition, Subtraction

# GROSS AND NET TOTALS
- Gross Total = Unit Price * quantity
- Net Total = Unit Price * quantity * (discount)

# SQL ORDER BY
```SQL
ORDER BY "Gross Total" DESC
```
- DESC: Is short for decending
- ASC: Is short for Ascending (this is default)

# SQL HAVING
```SQL
HAVING OrderID = x
```
# SQL GROUP BY
- GROUP BY: Order of the table

EXAMPLE:
```SQL
SELECT TOP 2 OrderID,
UnitPrice * Quantity * (1-Discount) AS "Net Total"
FROM [Order Details]
ORDER BY "Net Total" DESC
```

# SQL SELECT statement - Logical(syntax) sequence
- SELECT
- DISTINCT
- FROM
- WHERE
- GROUP BY
- HAVING
- ORDER BY

# STRING FUNCTIONS

- SUBSTRING : SUBSTRING (expression,start,length)
  SUBSTRING(name,1,1) for the initial

SELECT SUBSTRING ('my book',1,4) AS EXTRASTRING = my b

- CHARINDEX('a','text') to search for a string e.g. find 'a' in a column called 'text'

SELECT CHARINDEX ('O','Customer') = 5

- LEFT OR RIGHT: ex: LEFT(NAME,5) for the first 5 characters
                     RIGHT(TUTORIAL,3) for the last 3 characters

- LTRIM OR RTRIM: Used to remove spaces at the begining (LTRIM) or end of string (RTRIM)

- LEN: LEN(Name) for the length of the names

- REPLACE: REPLACE(name,'','_ ') to replace with underscores

- UPPER or LOWER: UPPER(name) to convert to all upper       

# DATE FUNCTIONS

- GETDATE: SELECT GETDATE() to return current date and time

- SYSDATETIME: SELECT SYSDATETIME() to return the date time of the computer being used

- DATEADD: DATEADD(d,5,OrderDate) AS "Due Date" to add 5 days

- DATEDIFF: DATEDIFF(d,OrderDate,ShippedDate) AS "Ship Time" ;to calculate difference between dates

- YEAR: SELECT YEAR(OrderDate) AS "Order Year" ;to extract the year from a date

- MONTH: SELECT MONTH(OrderDate) AS "Order Month" ;to extract the month from a date

- DAY: SELECT DAY(OrderDate) AS "OrderDate" AS "Order Day" ; to extract the day from the date

# DATE EXAMPLE
```SQL
SELECT DATEDIFF(yyyy, BirthDate, GETDATE()) AS "Age",
CASE
WHEN DATEDIFF(yyyy, BirthDate, GETDATE())>65
THEN 'Retired'
WHEN DATEDIFF(yyyy, BirthDate, GETDATE())>60
THEN 'Retirement Due'
ELSE 'More than 5 years to go'
END AS 'Retirement status'
FROM Employees;
```
# EXAMPLES
SELECT postalcode AS "post Code",
LEFT (PostalCode, CHARINDEX(' ',PostalCode)-1) AS "postal Code region",
CHARINDEX(' ',postalCode) AS "Space Found", Country
FROM Customers
WHERE Country = 'UK'


Q1)
```SQL
SELECT TOP 2 OrderID,
UnitPrice * Quantity * (1-Discount) AS "Net Total"
FROM [Order Details]
ORDER BY "Net Total" DESC
```
OR WITHOUT TOP 2, to find out full list

q2) Use CHAIRINDEX to list only product Names that contain a single quote.
note: Column Alias cannot be used in a WHERE
For single quote use two single quotes to 'escape' it

```SQL
SELECT p.ProductName
FROM Products p
WHERE CHARINDEX('''',P.ProductName)>0
```

q3)
```SQL
SELECT SupplierID,
SUM(UnitsOnOrder) AS "Total on Order",
AVG(UnitsOnOrder) AS "AVG on order",
MIN(UnitsOnOrder) AS "Max On order"
FROM Products
GROUP BY SupplierID
```

# JOINS
JOIN is an SQL keyword used to combine matched rows from two or more tables

- INNER JOIN = P(A intersecting B)

- LEFT JOIN or LEFT OUTER JOIN : P(A)

- RIGHT JOIN or RIGHT OUTER JOIN : P(B)

- FULL JOIN or FULL OUTER JOIN : P(A UNION B)

example question)
List Orders from the Orders table and JOIN to the customers and Employees tables to include Customer Name (Company Name) and employee Name (First and Last name)

```SQL
SELECT o.OrderID,o.OrderDate, o.Freight,e.FirstName+' '+e.LastName AS "Employee Name", c.CompanyName
FROM Orders o
INNER JOIN Customers c ON o.CustomerID=c.CustomerID
INNER JOIN Employees e ON o.EmployeeID=c=e.EmployeeID
```

# SQL (Structured Query Language)
- How to CREATE a DATABASE and USE it.

```SQL
CREATE DATABASE samir_db

USE samir_db
```
- How to CREATE a TABLE with COLUMS.



``` SQL
CREATE TABLE film_table
(
   film_id INT IDENTITY(1,1),
   film_name VARCHAR(20),
   film_type VARCHAR(12),
   date_of_release DATE,
   director VARCHAR(15),
   writer VARCHAR(15),
   star VARCHAR(15),
   film_language VARCHAR(15),
   website VARCHAR(MAX),
   plot_summary VARCHAR(MAX)
)
```

- How to ALTER a TABLE, adding a new COLUMN with Data Type INT.

``` SQL
ALTER TABLE film_table
ADD ratings INT
```
- How to VIEW the TABLE'S COLUMNS

```SQL
SP_HELP film_table
```

- How to INSERT ROWS (VALUES) into a TABLE.

```SQL
INSERT INTO film_table
(
   film_name, film_type, date_of_release, director
)
VALUES
(
   'JOHN WICK', 'ACTION', '20150410', 'Chad Stahelski'
)
```
- Show the TABLE.

```SQL
SELECT * FROM film_table
```
