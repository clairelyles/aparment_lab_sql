# Apartment lab

- Create a database called apartmentlab 
- Using this database, create two tables, one for owners and one for properties
- Keep this relationship in mind when designing your schema:
	+ **One owner can have many properties**

###Tables

- The owners table should consist of: 
	+ owner_id (this should be the primary key as well as a unique number that increments automatically)
	+ name
	+ age
- The properties table should consist of:
	+ property_id (this should be the primary key as well as a unique number that increments automatically)
	+ name
	+ number of units
	+ owner_id (this should have the constraint NOT NULL)
		+ There should be also be a foreign key that references the owners table

###Questions
Write down the following sql statements that are required to solve the following tasks.

Steps to a DB

1. CREATE DATABASE apartmentlab;
2. \connect apartmentlab
3. How to add the references from one table to another***
	CREATE a TABLE (property_id SERIAL PRIMARY KEY, name TEXT, units INT, INT REFERENCES owners(owner_id));

/////////////////////////////////////////////////////

###Lab Questions

1. Show all the tables.
	\dt

2. Show all the users. 
	SELECT USER;
	// clairelyles (name of comp)

	OR

	\du shows

3. Show all the data in the owners table.
	SELECT * FROM owners;

4. Show the names of all owners. 
	SELECT name FROM owners;

5. Show the ages of all of the owners in ascending order.
	SELECT age FROM owners ORDER BY age ASC;
	* DESC for descending

6. Show the name of an owner whose name is Donald. 
	SELECT * FROM owners WHERE name = 'Claire Lyles';

7. Show the age of all owners who are older than 30. 
	SELECT name, age FROM owners WHERE age > 30;

8. Show the name of all owners whose name starts with an E.
	SELECT name FROM owners WHERE name LIKE '%e%';

9. Add an owner named John who is 33 years old to the owners table.
	INSERT INTO owners (name, age) VALUES ('John', 33);

10. Add an owner named Jane who is 43 years old to the owners table. 
	INSERT INTO owners
	(name, age)
	VALUES
	('John', 33);

11. Change Jane's age to 30. 
	UPDATE owners SET age=30 WHERE name='Jane';

12. Change Jane's name to Janet. 
	UPDATE owners SET name='Janet' WHERE name='Jane';

13. Add a property named Archstone that has 20 units. 
	INSERT INTO properties
	(name, units, owner_id)
	VALUES
	('Archstone', 20, 3);

14. Delete the owner named Jane.
	DELETE from owners WHERE name = 'Janet';

15. Show all of the properties in alphabetical order that are not named Archstone and do not have an id of 3 or 5.
	SELECT name FROM properties WHERE name <>
	'Archstone' AND
	property_id  NOT IN (3,5)
	ORDER BY name ASC;

16. Count the total number of rows in the properties table.
	SELECT COUNT(*) FROM properties;

17. Show the highest age of all owners.
	SELECT MAX(age) FROM properties;

18. Show the names of the first three owners in your owners table.

SELECT * FROM owners JOIN properties ON owners.property_id = propoerty_id

###More Exercizes

SELECT * FROM subjects JOIN books ON books.subject_id = subjects.id WHERE subject ILIKE '%children%';

SELECT * FROM subjects JOIN books ON books.subject_id = subjects.id JOIN authors ON books.author_id = author.id WHERE subject ILIKE '%children%';
	

SELECT * FROM editions WHERE book_id=1590; but who published it? How many?

look up each addition, then from each addition, find out how many there are.


```
Bonus (this might require you to look up documentation online)

```
1. In the properties table change the name of the column "name" to "property_name". 
2. Count the total number of properties where the owner_id is between 1 and 3.
```
