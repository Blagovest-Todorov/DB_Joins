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

	
