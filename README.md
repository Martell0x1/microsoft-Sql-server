## What's A database
- a database is an organized collection of data so that it can be easily accessed.
- To manage these databases , Databases Mangment System (DBMS) are used

# Types of DBMS
- non-relational (DBMS): file , json , xml...
- relational (RDBMS): mysql , sql-server Oracle...

# why databases
- the dealing with normal files(DBMS) is so hard compared with databases(RDBMS).

- row = entity = record
- column = field = attribute = feature
- table = Entity set

## Data vs Information vs Knowledge vs wisdom
	# Data vs Information
		- A data is raw facts
		- information is data in context(insigts from this data)
		- Data + Meaning = Information
		- data is unstructured , info is structered
		- data is unanalized m info is analyzed
	# Wisdom vs Knowledge
		- information with time = knowledge
		- knowledge with practice (applied) = wisdom
## database essintials

# what is null.
	- null = nothing ( has no value , missing)
	- null != 0 or blank space
	- it's distinct value in database
	- if the attribute is optional is set to null

# Primary key vs Foreign Key
- a primary key is a unique identifier for a record(row) , each primary key in each row must be unique (something such as ID column in database is considerd a primary key) , it must not be null , the primary key could be 2 attributes , but it will be slow in searching (so to be more practical consider thinking in 1 attribute to be a primary key) , the VARCHAR datatype couldn't be a primary key (it must be INT) as it will slow down the database seach operations , it will take a large space , each table in the RDB must have a primary key , it's value can't be change

- Foreign key ... it's a  column or set of columns that refere to a primary key in other table , it establishes a relationship between two tables , allowing data to be shared and linked between them.

# Referential Integrity (Data Integrity)
- The foriegn key ensures that referential integrity is maintained by ensuring that any value in the foreign key column must exist in the primary key column of the related table.
	 
- imagine you have a table with the following attributes , ID , Name , Department Id and another table with the attributes Id , Name , Location .... the first table relates to the second table as the Department id in the first table is referencing to the id in the second table .... imagine a situation when you set a department id that doesn't exist in the second table ... this will cause an exception saying that this `foreign key` doesn't refere to that wrong primary key in the second table , so the data integrity is a concept ensures that the `referential integrity` is satisfied (each foreign key must refer to a primary key) , and that the difference between file systems and DBMS.

# Cascade Delete
- Deleting any record with the primary key in the second table the is refered by a foriegn key in the first table , so any record with the foreign key refered to the primary key that have been deleted in the second table .. it will be removed (and that's a big problem)