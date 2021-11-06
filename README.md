# DB_Joins
Joins, what is join, types
A Join clause is used to combine rows from two tables , based on a related column between them.


JOIN > allow us to access data of two and more table with one query by common column(condition column,) for the whole tables.
INNER and OUTER  join differ by the attitude to the NULL value.
OUTER Join -> Left jojin, right Join,
Left join –all records from the left table ant all the mating records of the right table.
Left table is the one that is in the FROM Clause of the Query, the right table is after the word join.,
Join condition is after the word on.
Right join takes all records in the right and all the records that fulfill the condition from the left.


 SELECT 
      MountainRange, 
	  PeakName, 
	  Elevation 
    FROM Mountains AS m
  JOIN Peaks AS p ON m.Id = p.MountainId
  
  join -gives aresult rows of two tables based on common colum into the two tab les
  ////
  
  SELECT 
      MountainRange, 
	  PeakName, 
	  Elevation 
    FROM Mountains AS m
  JOIN Peaks AS p ON m.Id = p.MountainId
  WHERE m.MountainRange = 'Rila'
  ORDER BY p.Elevation DESC
////

CREATE TABLE Passports
(
PassID INT PRIMARY KEY,
PassNumber CHAR(8) NOT NULL
)

ALTER TABLE Persons
ADD Constraint FK_Persons_Passports FOREIGN KEY(PassID) 
                                    REFERENCES Passports(PassID)

ALTER TABLE Persons
        ADD UNIQUE(PassID)

ALTER TABLE Passports
		ADD UNIQUE (PassNumber)

INSERT INTO 
        Passports(PassID, PassNumber)
VALUES
        (104, 'N34FG21B')
		--(102,'K65LO4R7'),
		--(103, 'ZE657QP2')


INSERT INTO Persons (PersonID, FirstName, Salary, PassID)
VALUES
    (1, 'Roberto', 43300.00, 102),
	(2, 'Tom',56100.00, 103),
	(3, 'Yana', 60200.00, 101)

	///
	EXAMPLE :
	
	USE SoftUni
SELECT
     * 
    FROM 
	   Employees AS e
    INNER JOIN Departments AS d ON e.DepartmentID = d.DepartmentID
    
    ///
    
SELECT * FROM Employees AS e 
LEFT OUTER JOIN Departments AS d
      ON e.DepartmentID  = d.DepartmentID
	  WHERE d.DepartmentID IS NOT NULL
	  
	  
	  
	  /////////
	  SELECT TOP(50) e.FirstName, e.LastName, t.[Name] AS Town, a.AddressText 
          FROM Employees AS e
          JOIN Addresses AS a ON e.AddressID = a.AddressID 
          JOIN Towns AS t ON a.TownID = t.TownID
	  ORDER BY FirstName, LastName


////

SELECT TOP 5
    e.EmployeeID,
	e.JobTitle,
	a.AddressID,
	a.AddressText
 FROM Employees AS e 
 JOIN Addresses AS a ON e.AddressID = a.AddressID
 ORDER BY a.AddressID ASC
 ///
	
SELECT 
   e.EmployeeID, 
   e.FirstName,
  --p.StartDate,
   CASE
   WHEN YEAR(p.StartDate) >= 2005 THEN NULL
   ELSE p.[Name]
   END AS ProjectName
FROM Employees AS e
JOIN EmployeesProjects AS ep ON e.EmployeeID = ep.EmployeeID
JOIN Projects AS p ON ep.ProjectID = p.ProjectID
WHERE ep.EmployeeID = 24


//

Problem 16./SOFTUNI	Countries without any Mountains
Write a query that selects CountryCode. Find all the count of all countries, which don’t have a mountain.
Example


SELECT COUNT(c.CountryCode) AS CountryCode
FROM Countries AS c
  LEFT JOIN MountainsCountries AS mc ON mc.CountryCode = c.CountryCode
  --LEFT JOIN Mountains AS m ON m.Id = mc.MountainId
  WHERE mc.MountainId IS NULL

	
