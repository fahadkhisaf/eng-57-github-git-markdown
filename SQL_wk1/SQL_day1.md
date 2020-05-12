# Week1, day 1 SQL

# Primary key
- Primary key uniquely identify a record in the table.
- Primary Key can't accept null values.
- By default, Primary key is clustered index and data in the database table is physically organized in the sequence of clustered index.
- We can have only one Primary key in a table.

# Foreign key
- Foreign key is a field in the table that is primary key in another table.
- Foreign key can accept multiple null value.
- Foreign key do not automatically create an index, clustered or non-clustered. You can manually create an index on foreign key.
- We can have more than one foreign key in a table.

# One to One
- Use a foreign key to the referenced table
student: student_id, first_name, last_name, address_id
address: address_id, address, city, zipcode, student_id

# One to many
- Use foreign key on the many side of the relationship linking back to the 'one' side
teachers: teacher_id, first_name, last_name - the 'one' side
classes:  class_id, class_name, teacher_id - the 'many' side

# Many to many
- Use junction table
student: student_id, first_name, last_name
classes: class_id, name, teacher_id
student_classes: class_id, student_id     # the junction table

# Structered query language
- DML(Data control language): select, insert, update, delete
- DDL(Data defination language): Create, alter, drop, truncate
- DCL(Data control language): Grant, revoke
- TCL(Transaction control language): commit, rollbacl, savepoint

# Data types
- VARCHAR: Adaptable to different lengths of characters. Records MAX size
- CHARACTER or CHAR: Data must be at fixed length.Fixed amount of space used
- INT: Holds a whole number/integer value
- DATE or TIME or DATETIME: Stores Date, Time or both date and time
- DECIMAL or NUMERIC: Fixed precision and scale (digits to right of decimal point) numbers.
- BINARY: Use to sotre binary data such as an image or file.
- FLOAT: Equivalent to binary (0,1 or NULL)

# SQL 
'''SQL
USE fahad_K_db

CREATE TABLE film_table1

CREATE TABLE film_tab
(
    film_id INT IDENTITY(1,1),
    film_name VARCHAR(20),
    film_type VARCHAR(10),
    date_of_release DATETIME,
    director_name VARCHAR(10),
    writer_name VARCHAR(10),
    star_cast VARCHAR(10),
    film_language VARCHAR(10),
    official_website VARCHAR(30),
    plot_summary VARCHAR(max)



);

INSERT INTO film_tab
(
    film_name,film_type, plot_summary


)
VALUES
(
    'Geo-Storm', 'sci-fi', 'maximum'
)
