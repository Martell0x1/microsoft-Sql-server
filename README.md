# Quick Access
- [What is a Database](#whats-a-database)
    - [Types of DBMS](#types-of-dbms)
    - [Why Databases](#why-databases)
    - [Data vs Information vs Knowledge vs Wisdom](#data-vs-information-vs-knowledge-vs-wisdom)
- [Database Essentials](#database-essentials)
    - [What is Null](#what-is-null)
    - [Primary Key vs Foreign Key](#primary-key-vs-foreign-key)
    - [Referential Integrity (Data Integrity)](#referential-integrity-data-integrity)
    - [Cascade Delete](#cascade-delete)
    - [Data Redundancy (Data Duplications)](#data-redundancy-data-duplicatons)
    - [Data Integrity](#data-integrity)
    - [Constraints](#constraints)
    - [SQL (Structured Query Language)](#sql-structured-query-language)
- [Database Design](#database-design)
    - [ERD (Entity Relationship Diagram)](#erd-entity-relationship-diagram)
    - [ERD Symbols](#erd-symbols)
    - [Components of ER Diagram](#components-of-er-diagram)
    - [Entity vs Weak Entity](#entity-vs-weak-entity)
    - [Attributes](#attributes)
    - [Relationships](#relationships)
    - [Cardinality vs Ordinality](#cardinality-vs-ordinality)
    - [Cardinality Symbols](#cardinality-symbols)
    - [Total vs Partial Participation (OLD ERD)](#total-vs-partial-participation-old-erd)
    - [Process of Creating ERD](#process-of-creating-erd)
    - [Associative Entities / Aggregation](#associative-entities-aggregation)
    - [Generalization](#generalization)
    - [Specialization](#specialization)
- [Relational Schema](#relational-schema)
    - [Convert Self Referential](#convert-self-referential)
    - [Convert Composite / MultiValued / Derived Attributes](#convert-composite-multivalued-derived-attributes)
    - [Convert One-to-One Relationship](#convert-one-to-one-relationship)
    - [Convert One-to-Many Relationship](#convert-one-to-many-relationship)
    - [Convert Many-to-Many Relationship](#convert-many-to-many-relationship)
    - [Convert Generalization, Specialization](#convert-generalization-specialization)
    - [Convert Associative Entity](#convert-associative-entity)
    - [Summary](#summary)

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
    - relationships are being assigned depends on buissenes requiremenets.
    1. #### One-To-One relationship
        being written just like this in ERD diagram `[table1]--1--->(relationship)-----1--->[table2]`
        ex:
            1. student ----> id
            2. Student ----> person
            3. member ---> book (assuming that the buissenes requiremenets obligies me hat only one member can borrow only one book)
            4. Traveler ----> seat
            5. Employee ----> Desk
            6. Employee ----> phone Extention
            7. Employee -----> Task (said that the buissenes requirements obligies me that for each employee he takes only one task)
    2. #### One-To-Many / Many-To-One
        - when a single element of an entity is associated with more than one element of another entity , it's called a ont-to-many relationshipt.
        - it's being wriiten like this `[table1]---1--->(relation)---M--->[table2]` or vice-verca
        ex:
            1. customers --> order `[customer] ---- 1  --->(place) --- m--->[order]`
            2. order ---> customer `[order] ---- M  --->(ordered by) --- 1--->[customer]`
            3. Employee --> project `[Employee] ---- M  --->(works on) --- 1--->[project]`
            4. member ---> book `[member] ---- 1  --->(borrow) --- m--->[book]`
            5. cutomer ----> mobile line `[customer] --- 1--->(can have) --- m --->[mobile line]`

    3. #### Many-To-Many relationship
        you might guess it.

## Cardinality Vs Ordinality
- 1. Cardinality:
    - refers to the `Maximum` number of times an instance in one entity can relate to instances of another entity
    - Cardinality is used to determine the relationships among entites (one-to-one , ont-to-many , many-to-many)
- 2. Ordinality:
    - is the `Minimum` number of times an instace in one entity can be associated with an instance in the related entity, in other words it specifies if it's optional or mandatory

    - in ERD systems we can refere to the Cardinality and ordinalty as follwing `(ordinalty,Cardinality)`
   - ex:
        `[student]--<0>--(Enrolled)---<0>->[cource]` , in this paper we refer to the ordinalty in <> tags
            this ERD means that a student could enroll in acource or not so the student entity is optional to the cource entity, 
            a cource could have students or not so it's optional to the student entity.

        `[customer]----(1,1)---------<Place>--------(0,M)------>[order]` , a customer is required to place an order , but an order doesn't depend on a customer.

## Cardinality Symbols
- crow-s-foot-notation.
    [see this](https://vertabelo.com/blog/crow-s-foot-notation/)
- min-max-notation.
    [see this]()
- bachman-notaion.
    [see this]()

## Total Vs Partial Participation (OLD ERD)
- review ur course.
- total Participation = mandatory , Partial Participation = optional.

## Process of Creating ERD.
- note that the business requirements should be considered carefully.
-   1. Entity Identification => `Ask your self if this thing should have a data to be stored in the database?`
    2. Relationship Identification => `what is the relation between entity A and entity B`
    3. Cardinality Identification  => `what is the cradinality and ordinalty (min ,max)`
    4. Identify Attributes.
    5. Create ERD
## Erd site
- this site is pretty good for designing ERD [erdplus](https://erdplus.com/)

## Associative Entities / Aggregation
- an entity that comes up from connecting a relation with another relation.
- it's called `junction table` , `linking table` , `cross-reference table`.
- by using Aggregation / associative-entity , we can represent complex relationships between entities in a structured and efficeint way , without having to duplicate data or create confusing relationships and avoid data redundancy , making it a useful concept om database design.
- we call it Aggregation becouse when an entity has a relationship with another relationship , a relation with it's corresponding entities is Aggregated into a higher level entity. Aggregation is an abstract through which we can represent relationship as higher level entity set. 

- [see me](https://www.sciencedirect.com/topics/computer-science/associative-entity)

## Generalization.
- when we have more than one entity that share many attributes , we can make another entity and make thos entities inherite the base entity usnig the `bottom-up approach`
- it's represented in ERD using this traingle:
    `
        |
      /   \
     / IS  \
    /   A   \
   /---------\
` , please note that the head must be at top and the base must be at bottom.
- just remember that Generalization is just like inhertance in OOP
- ex `from student with name and age related with employee with name and age ==> to person who relates with both student and employee`
- [see me](https://technogeekscs.com/generalization-in-dbms/)

## Specialization.
- Specialization is a `top-down approach` in which a higher-level entity is divided into multiple specialized lower-level entities
- an entity is devided into sub entities with same charactristics.
- ex: `from employee to developer`, `from employee to teacher`,...etc

- it's represented in ERD using this traingle:
    `
    \--------/
     \  IS  /
      \  A /
       \  /
         |
`

# Relational Schema.
- a set of relational tables and associateed items that are related to each other.
- relation schema defines the design and structure of the relation like it consists of the relation name , set of attributes/fields , names/columns , every attribute would have an associated Domain

    ## convert Self Referntial.
    - if we though in the employee examble `(employee)------<manages>---->(employee)`
    - we then design it as follows: in the same table we add a foreign key field to the primary key of the table.
    - `
        Employee
        -----------------
        PK | EmpID 
           | Name   
           | Salary
        FK | ManagerID
        ------------------
    `

    ## convert Composite / MultiValued / Derived Attributes
    - in composite attribute we take the roots of the tree ex , name-> firstname, lastname , we take firstname and lastname as attributes
    - in derived attribute we ignore it.
    - in mutlivalued attributes we make a new entity for it and the public key of the original entity has a foreign key to that table with the same name

    ex:
        `(student)
            (<stdudentID>) , (name)->((firstname),(lastname)) , (/age/) , ((phone))`
        - we have studentId as a primary key , name as a composite attribute , age as a derived ,, phone as mutlivalued
        - so this becomes this
        `
            Student                             Phone
            ---------------------               -------------
            PK  |   StudentId   |----------       Pk | PhoneID
                |   Firstname   |         |          | Phone
                |   LastName    |         |-----> FK | StudentID
            ---------------------               ---------------
        `
    ## Convert one-to-one relationship
    - take one of the primary key of one entity and put it as a foriegn key in the second table or vice-versa
    - ex:
        `Employee <-----> Acess-card`
        - first solution
            `
                Employee                AcessCard
                ---------               -----------
                PK  | EmployeeID ----   PK  | CardId
                    | Name          |       | serial num
                    ...              -> FK  | EmployeeID
                ------------            ------------------
            `
        - second solution (this is prefered)
            `
                Employee            AcessCard
                ------------        ---------
                PK  | EmpID    ---- PK | cardID
                    | Name     |       | Serial num
                FK  | CardID  <-     ----------------
            `
    ## Convert One-to-Many relationship.

    - ex:
        `Employee <<<--(works in)---> Department`

    ## convert Many-to-Many relationship
    - when deailing with many-to-many relationships , you must consider creating the `Bridge Table`, that has the public keys of both other tables as a foreign keys
    - ![Many-To-Many-Relational-Schema] (https://www3.ntu.edu.sg/home/ehchua/programming/sql/images/ManyToMany.png)
    - the middle table is called `Bridge table / Bridge Entity`

    - note that in the bridge table the tow foriegn keys must be foriegn keys not primary keys , imagine the system when having a student can enroll in course , so we will end up with 3 tables (student , enrollment , course) , if we take the tow primary keys of the tow other tables and put them as a primary keys in the enrolmment table , an edge case will be ingored which is when a student fails in a course he can retake it , but with using the primary keys this will not be able to be achieved , as the primary key is unqiue.

    ## Covert Generalization , Specialization.
    - Take the Primary key from parent and put it in the child as a forign key.
    
    ## Convert Assocative Entity.
    - same as converting many-to-many , but here there will be another table related with the associative entity , we will take it's primary key and put it as a foreign key in the Bridge Entity.

    - ![Associative] (https://miro.medium.com/v2/resize:fit:704/1*-h54ZLPXdamjmtqRqk_8PQ.png)

    ## Summary
    - Self-Refrential               One Entity that have a foriegn key that points to thye primary key
    - Attributes                    ignore the derived attribute , take the childs of the composit attributes , create a new table for the mutlivalued attrivutes.
    - Generalization , Specailization   Take the Primary key of the parent and put it as a foreign key in the child.
    - One-To-One                    take one of the primary key of one entity and put it as a foriegn key in the second table or vice-versa
    - One-To-many / Many-To-One     take the primary key of one side and put it as a forign key in the many  side.
    - many-to-many                  Create a Bridge Table , take the primary key of the tow talbes , put them as a foriegn key in the bridge table
    - Assocative                    same as many-to-many , but now you have to add other tables to the bridge table.

# SQL
- in this section we wil put our hands on SQL queires using SQL-Server-Managment-Studio
- The System-databases in SSMS is used to makes you able to excute commands and some other internal stuff, don't fuck with it.
    ## DDL
    - DDL = Data Defineation language.
    ### CREATE_DATABASE
    - on the databases section just write click and select new database , give it a name and press ok , this is the GUI way to create it
    - another way is to use the DDL to create it , select "new Query" and type this query `CREATE DATABASE DB_NAME;` , then hit excute button , and write click on the databases and refresh , it will appear.
    ### CREATE_DATABASE_IF_NOT_EXIST
    - checks if the databases is not exist if not so it will create it .
    - syntax `IF NOT EXISTS(SELECT * FROM sys.databases WHERE name = 'db_name') <br>`
                     ` BEGIN<br>`
                        ` CREATE DATABASE db_name;<br>`
                     `END`




