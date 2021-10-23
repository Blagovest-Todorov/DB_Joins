# DB_Joins
Joins, what is join, types
A Join clause is used to combine rows from two tables , based on a related column between them.

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
