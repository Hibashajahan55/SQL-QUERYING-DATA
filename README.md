# SQL- QUERYING DATA
# SQL Queries for Country and Persons Tables
# INTRODUCTION
This project demonstrates SQL queries on two tables: Country and Persons. The dataset includes country information such as population and area, as well as personal information with ratings and country associations. Below is the schema for both tables, along with the queries performed on the data.
## TABLE STRUCTURE
#### Country Table Structure
* Id: INT (Primary Key) – Unique identifier for each country.
* Country_name: VARCHAR(100) – Name of the country.
* Population: BIGINT – Population of the country.
* Area: INT – Area of the country in square kilometers.
#### Persons Table Structure
* Id: INT (Primary Key) – Unique identifier for each person.
* Fname: VARCHAR(255) – First name of the person.
* Lname: VARCHAR(255) – Last name of the person.
* Population: BIGINT – Population of the person’s country.
* Rating: DECIMAL(3, 2) – Rating of the person (e.g., 4.5).
* Country_Id: INT (Foreign Key) – References the Id field in the Country table.
* Country_name: VARCHAR(255) – Name of the person’s country.

## TASKS
1. List the distinct country names from the Persons table
2. Select first names and last names from the Persons table with aliases.
3. Find all persons with a rating greater than 4.0.
4. Find countries with a population greater than 10 lakhs.
5. Find persons who are from 'USA' or have a rating greater than 4.5.
6. Find all persons where the country name is NULL.
7. Find all persons from the countries 'USA', 'Canada', and 'UK'.
8. Find all persons not from the countries 'India' and 'Australia'.
9. Find all countries with a population between 5 lakhs and 20 lakhs.
10. Find all countries whose names do not start with 'C'
## QUERIES

### Create Country table
CREATE TABLE Country (
    Id INT PRIMARY KEY,
    Country_name VARCHAR(100),
    Population BIGINT,
    Area INT
);


### Create Persons table
CREATE TABLE Persons (
    Id INT PRIMARY KEY,
    Fname VARCHAR(100),
    Lname VARCHAR(100),
    Population INT,
    Rating DECIMAL(3, 2),
    Country_Id INT,
    Country_name VARCHAR(100),
    FOREIGN KEY (Country_Id) REFERENCES Country(Id)
);


### Insert data into Country table
INSERT INTO Country (Id, Country_name, Population, Area)
VALUES 
(1, 'USA', 75000000, 9833520),
(2, 'India', 5000000, 3287263),
(3, 'Canada', 8000000, 9984670),
(4, 'UK', 150000000, 243610),
(5, 'Australia', 400000, 7692024),
(6, 'Germany', 2000000, 357022),
(7, 'France', 6900000, 551695),
(8, 'Brazil', 6000000, 8515767),
(9, 'Russia', 15500000, 17098242),
(10, 'Japan', 8650000, 377930);



### Insert data into Persons table
INSERT INTO Persons (Id, Fname, Lname, Population, Rating, Country_Id, Country_name)
VALUES
(1, 'Jeeva', 'Joseph', 75000000, 4.5, 1, 'USA'),
(2, 'Arya', 'Shan', 5000000, 3.8, 2, 'India'),
(3, 'Emma', 'Emmi', 8000000, 4.9, 3, 'Canada'),
(4, 'Basim', 'Johny', 150000000, 4.2, 4, 'UK'),
(5, 'Aryan', 'John', 400000, 3.9, 5, 'Australia'),
(6, 'Maria', 'Grace', 2000000, 4.7, 6, 'Germany'),
(7, 'James', 'Wilson', 6900000, 2.1, 7, 'France'),
(8, 'Suzzy', 'Martin', 6000000, 4.0, 8, 'Brazil'),
(9, 'Robert', 'Williams', 15500000, 1.7, 9, 'Russia'),
(10, 'Jane', 'Taylor', 8650000, 4.6, 10, 'Japan');
select * from persons;

###  (1)List the distinct country names from the Persons table
SELECT DISTINCT Country_name FROM Persons;

###  (2)Select first names and last names from the Persons table with aliases.
SELECT Fname AS First_Name, Lname AS Last_Name FROM Persons;

### (3)Find all persons with a rating greater than 4.0. 
SELECT * FROM Persons WHERE Rating > 4.0 ;

### (4)Find countries with a population greater than 10 lakhs. 
SELECT * FROM country WHERE Population > 1000000 ;

### (5)Find persons who are from 'USA' or have a rating greater than 4.5.
SELECT * FROM Persons 
WHERE Country_name = 'USA' OR Rating > 4.5;

###  (6)Find all persons where the country name is NULL.
SELECT * FROM Persons 
WHERE Country_name IS NULL;

###  (7)Find all persons from the countries 'USA', 'Canada', and 'UK'.
SELECT * FROM Persons 
WHERE Country_name IN ('USA', 'Canada', 'UK');

###  (8)Find all persons not from the countries 'India' and 'Australia'. 
SELECT * FROM Persons 
WHERE Country_name NOT IN ('India', 'Australia');

### (9)Find all countries with a population between 5 lakh and 2 lakhs
SELECT * FROM Country 
WHERE Population BETWEEN 500000 AND 2000000;

### (10)Find all countries whose names do not start with 'C'.
SELECT * FROM Country 
WHERE Country_name NOT LIKE 'C%';
