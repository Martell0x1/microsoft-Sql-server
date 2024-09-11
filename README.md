# What's A database
- a database is an organized collection of data so that it can be easily accessed.
- To manage these databases , Databases Mangment System (DBMS) are used

## Types of DBMS
- non-relational (DBMS): file , json , xml...
- relational (RDBMS): mysql , sql-server Oracle...

## why databases
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
# database essintials

## what is null.
	- null = nothing ( has no value , missing)
	- null != 0 or blank space
	- it's distinct value in database
	- if the attribute is optional is set to null

## Primary key vs Foreign Key
- a primary key is a unique identifier for a record(row) , each primary key in each row must be unique (something such as ID column in database is considerd a primary key) , it must not be null , the primary key could be 2 attributes , but it will be slow in searching (so to be more practical consider thinking in 1 attribute to be a primary key) , the VARCHAR datatype couldn't be a primary key (it must be INT) as it will slow down the database seach operations , it will take a large space , each table in the RDB must have a primary key , it's value can't be change

- Foreign key ... it's a  column or set of columns that refere to a primary key in other table , it establishes a relationship between two tables , allowing data to be shared and linked between them.

## Referential Integrity (Data Integrity)
- The foriegn key ensures that referential integrity is maintained by ensuring that any value in the foreign key column must exist in the primary key column of the related table.
	 
- imagine you have a table with the following attributes , ID , Name , Department Id and another table with the attributes Id , Name , Location .... the first table relates to the second table as the Department id in the first table is referencing to the id in the second table .... imagine a situation when you set a department id that doesn't exist in the second table ... this will cause an exception saying that this `foreign key` doesn't refere to that wrong primary key in the second table , so the data integrity is a concept ensures that the `referential integrity` is satisfied (each foreign key must refer to a primary key) , and that the difference between file systems and DBMS.

## Cascade Delete
- Deleting any record with the primary key in the second table the is refered by a foriegn key in the first table , so any record with the foreign key refered to the primary key that have been deleted in the second table .. it will be removed (and that's a big problem)


## Data Redundancy (Data Dublications)
- Redundancy of data is the presence od duplicayed copies of data within the database.

-it can also cause problems. For example, redundant data takes up additional storage space and can make it more difficult to maintain consistency within the database. If one copy of the data is updated, the other copies may become outdated, leading to inconsistencies and errors.

- Redundancy can occur through several ways ... the inconsistent(bad) design of database , insertion of multiple copies of data , storing information that can be derived from other data in the database (good redundancy) ...if you want to make a company database with different department and each department has a number of employees you count the number of emps in the run time of application "using SELECT" statment , or you can create a column contains the number of emps in that department, this will be faster , that's why this is considered as good redundancy.

- To avoid redundancy in DBs , [Normalization] techniques can be used to organize the data in a way that minimizes duplication.

- Normalization is the process of organizing data in a database in a way that reduces redundancy and improves integrity , This involves breaking down the data into smaller , more atomic pieces and linking them together through relationships , which can reduce the amount of redundant data and make it easier ti manage and update the database , Additionally enforcing [data_constrains] such as unique keys and foreign key relationships , can help prevent redundant data from being insetrted into the database.

## Data Integrity
- Data integrity refers to the accurace , consistency and reliability of data over the entire life cycle , from the creation to deletion, it referse to the assurance that data is complete , accurate , and trustworthy.

- there are several factors that can impact data integrity , including human errors , hardware or software failure , security breaches and transfer errors.
- to maintain data integreity , it is important to establish appropriate policies and procedures , and to implement appropriate technologies , such as encryption , backups , access controls.

- Data Corrpution - happens when data imegration(when switching from an old system to an old one)

- There're different types of data integrity that organizations need to consider:
	- Entity Integrity: this ensures that each record / row in the table is unqiye and can be uniquely identified , using the primary keys
	- Referential Integrity: This ensures that relationships between tables are maintained and that there're no orphaned records , using the foreign keys.
	- Domain Integrity: This ensures that data is within acceptable ranges or values , Ex. a age field should only contain valid numeric values.
	- Business integrity : Ensuring that data meets business rules and requirements , a bank might have rules around minimum and macimum account balances.

- To maintain data Integrity we use [Constrains].

## Constraints
- rules or conditions that are applied to the data to ensure it's integrity and consistency.
- Constrains can be applied to individual columns or entire tables, they used to enforce various rules and restrictions on the data

- by using constraints , you can ensure that your data is accurate , consistent , easy to manage.

- Types of constraints:
	- Primary-key Constraint: this constraint ensures that a column or a set of columns uniquely identifies each row in a table , this constraint helps to enforce data integrity and ensure that there are no duplicated rows in the table.

	- Foreign-key Constraint: This constraint establishes a relation between tow tables based on a key field , it ensures that data in one table matches data in other table , and it helps to maintain refrential integrity in the database.

	- Unique Constraint: This constraint ensures that a column or a set of columns is unqie across all rows in the table , it helps to enforce data integrity and prevent duplicated rows in the table

	[!NOTE] > Unique Constraint Vs Primary-Key constraint?
		The unqie constraint is just like the primary key constraint except that the unique constraint can accept NULL values , however the Primary-key constraint does not.
	
	- Not-Null Constraint: This constraint ensures that a column or a set of columns doesnt have a null (empty) values , it helps to ensure that data is compelete and accurate

	- Check Constraint: This is more general constraint that ensures that data in a column or set of columns meets a specified condition.


## SQL (Structued Query Language)
- SQL is used to communicate with a database.
- SQL lets you access and manipulcate database.
- Oracle , Sybase , Ms-sql-server , Access , Ingres , etc...

- Types of Sql Statments:
	- DDL = Data Definition Language (CREATE , DROP , ALTER , TRUNCATE)
	- DML = Data Manipulation Language (INSERT , UPDATE , DELETE)
	- DCL = Data Control Language (GRANT,REVOKE)
	- TCL = Transaction Control Language (COMMIT , ROLLBACK , SAVEPOINT)
	- DQL = Data Query Language (SELECT)

# Database Design.
## ERD (Entity Relationship diagram)
- A Diagram to show the full overview on my system database , it's explains the relationship between entities to be stored in a database, it's like UML diagram or C4 diagram
- the ERD (ER) Diagram is the structure of the database , It acts as a franework (blueprint) with specialized symbols for the purpose of defining the relationship between the databaase entities.
- ER diagram is created based on three principal components: (Entities , attricbutes , Relationshhips)
- A one must consider the good practice and spend lots of time in the planning and designing stage

- Er Modeling (Entity-Relation Modeling) represents the structre of the database with the help pf diagram.
- ER modeling is a systematic process to degign a database as it would require you to analze all data requiremenets before implementing your database.

## ERD Symbols
- Entity = rectangle... strong Entity (Entity with primary key)
 - To identify the Entity , ask your self a question , do i need to store informations for that entity? if yes so it's a entity
 - The 2 nested 2 rectangles = weak Entity (it has no primary key , prefered not using it)
- Relation = diamond and lines

- the Ellipses = attribute.
	- if the attribute has more than 1 type , ie. name (first , mid , last) = composite attribute.
	- the 2 nested Ellipses = multivalued attribute ( prefered not to say)


- the doted Ellipses = derived attribute (some attribute  is optional , i can derive it fomr another data , like age , employees number...etc)
- the underscore = primary key (key attribute)


## Components of ER Diagram
- ER diagram is based on 3 basic concepts:
	* Entitis:
		- Entity (Strong)
		- Weak
	* Attributes:
		- Attribute
		- Key Attribute
		- Composite Attribute
		- Multivalued Attribute
		- Derived Attribute
	* Relationships:
		- one-to-one
		- one-to-many
		- many-to-one
		- many-to-many


## Entity vs Weak Enntity
- An Entity = row or record
- ex , A student Enrolled in course [student]-------(Enrolled)----->[courses]
- You can acheive Entity Integrity by having only strong Entities in ur ER diagram

## Attributes
-next

## Relationships
- at first we need to understand how to define a relationship between tow entities , think in the following examples:

    1. you have a university system , define the following relationship [student] -----(?)--->[course]
        - as you might gussed a student can enroll in an course [student] ----(enrolls in)--->[course]
    
    2. [student] ------(?)----->[id card] => [student]-----(has an)---->[id card]

    3. [employee]-------(?)---->[project] => this relation could be formated in more than 1 relation , you should consider drawing all possible relationships between entities , [employee]-----(works on)---->[project] `or` [employee]----(manages)--->[project]

    ### Self Referencing Relationship
        - some entities could have relations with themselfs such as employee , a manager can manage(employee) can manage other employees , so [employee]-----(manages)---->[employee]
        - imagine it just like  this table.
        '
             |ID |  Name   | Salary | Manager |
             |---|---------|--------|---------|
        |--> | 1 | Ahmed   | 5000   | NULL    |
        |    | 2 | Mohamed | 1300   | 1       |----|
        |    | 3 | Ali     | 1200   | 2       |    |
        -------------------------------------------|
        '
    ### Relation Types
    - next
