# Content

1. [Chapter 1: MySQL](#chapter1)
    - [Chapter 1 - Part 1: Create User](#chapter1part1)
    - [Chapter 1 - Part 2: Login User MySQL](#chapter1part2)
    - [Chapter 1 - Part 3: Create Database MySQL](#chapter1part3)
    - [Chapter 1 - Part 4: Data Type MySQL](#chapter1part4)
    - [Chapter 1 - Part 5: Project Modeling MySQL](#chapter1part5)

## <a name="chapter1"></a>Chapter 1: MySQL

#### <a name="chapter1part1"></a>Chapter 1 - Part 1: Create User


```sql

/* Enter in "MySQL 8.0 Command Line Client" */

/* Create a user - QUERY: create user (user name)@'%' identified by '(password)'; */

create user usermysqlexample@'%' identified by 'mysqlexample';

/* This user don't have permission to acess any database */

/* To give access for all databases to the created user we have to execute this query */

/* QUERY: grant all privileges on *.* to (user name)@'%' with grant option; */

grant all privileges on *.* to usermysqlexample@'%' with grant option;

/* The command "grant all" give access a global level to the user */

/* To revoke the acess to the user - QUERY: revoke all on *.* from usermysql; */

/* Example of Access Level */

/* Global Level (All Access) - QUERY: grant all on *.* to (user name)@localhost; */

/* Global Level (Revoke All Acess) - QUERY: revoke all on *.* from (user name); */

/* Database Level (Database Access) - QUERY: grant all to (database name).* to (user name)@localhost; */

/* Database Level (Revoke Database Acess) - QUERY: revoke all on (database name).*; */

/* Table Level (Table Access) - QUERY: grant all on (database name).(table name); */

/* Table Level (Revoke Table Acess) - QUERY: revoke all on (database name).(table name); */

/* Column Level (Column Access) - QUERY: grant select(column name),
										 insert(column name),
										 update(column name)
										 on (database name).(table name)
										 to (user name)@localhost
										 identified by (password);
*/

/* Column Level (Revoke Column Access) - QUERY: revoke select(column name),
												insert(column name),
												update(column name)
												on (database name).(table name)
												to (user name)@localhost
												identified by (password);
*/

/* Stored Routine Level (Routine Acess) - QUERY: grant routine on (database name).* to (user name)@localhost; */

/* Stored Routine Level (Revoke Routine Acess) - QUERY: revoke routine on (database name).* to (user name)@localhost; */

/* Stored Procedure Level (Procedure Acess) - QUERY: grant execute on procedure (database name).(procedure name) to (user name)@localhost; */

/* Stored Procedure Level (Revoke Procedure Acess) - QUERY: revoke execute on procedure (database name).(procedure name) to (user name)@localhost; */

```

#### <a name="chapter1part2"></a>Chapter 1 - Part 2: Login User MySQL

```sql

/* With the user created, we need to access him - QUERY: SYSTEM mysql -u (user name) -p */

/* After that, mysql will ask to enter the user password */

SYSTEM mysql -u usermysqlexample -p

/* To list all users - QUERY: select user, host from mysql.user; */

select user, host from mysql.user;

/* To confirm if the current user - QUERY: SELECT USER(); */

SELECT USER();

/* To use the root user - QUERY:  SYSTEM mysql -u root -p*/

/* After that, mysql will ask to enter the root password */

/* To delete user account - QUERY: DROP USER IF EXISTS '(user name)'@'localhost'; */

                       /* - QUERY: DROP USER IF EXISTS '(user name)'@'%'; */

DROP USER IF EXISTS 'usermysql'@'localhost';

```

#### <a name="chapter1part3"></a>Chapter 1 - Part 3: Create Database MySQL

```sql

/* Create Database - QUERY: create database (database name); */

create database example;

/* Show all databases in the system - QUERY: show databases; */

show databases;

/* After create a database, we need to use the database - QUERY: use (database name); */

use example;

/* To verify the current database we are using - QUERY: select database(); */

select database();

```
#### <a name="chapter1part4"></a>Chapter 1 - Part 4: Data Type MySQL

```sql
  
/* Data types in MySQL */

/* Text Type:
			CHAR(SIZE) - stores a fixed number of characters (up to 255 characters)
			
			VARCHAR (SIZE) - it has char-like features with the difference that if 
			you create with more than 255 characters, it transforms to the TEXT type (up to 255 characters)
			
			TEXT - stores strings  ((up to 65.535 characters)
			
			BLOB - can stores bytes. Use to store images (up to 65.535 byte file)
			
*/

/* Numeric Type:
			TINYINT - stores integer numbers (from -128 until 127 characters)
			
			SMALLINT - stores integer numbers (from -32768 until 32767 characters)
			
			MEDIUMINT - stores integer numbers (from -8388608 until 8388607 characters)
			
			INT(SIZE) - stores integer numbers (from -2147483648 until 2147483647 characters)
			
			BIGINT(SIZE) - stores integer numbers (from -9223372036854775808 until 9223372036854775807 characters)
			
			FLOAT(SIZE,DECIMAL) - stores real numbers
			
			DOUBLE(SIZE,DECIMAL) - stores real numbers. More than float
*/

/* Date/Time Type:
			DATE() - stores dates in the format YYYY-MM-DD. Y is Year, M is MONTH and D is Day.
			
			DATETIME() - stores dates in the format YYYY-MM-DD HH:MI:SS. Y is Year, M is MONTH and D is Day. H is hour, MI is minute and SS in seconds.
			
			TIME() - store time in H is hour, MI is minute and SS in seconds.
			
*/

```

#### <a name="chapter1part5"></a>Chapter 1 - Part 5: Project Modeling MySQL

```sql

/* CONCEPTUAL MODELING:
		
		 This Data Model defines WHAT the system contains. 
		 This model is typically created by Business stakeholders and Data Architects. 
		 The purpose is to organize, scope and define business concepts and rules.
			
*/

/* LOGICAL MODELING:
		
		 Defines HOW the system should be implemented regardless of the DBMS. 
		 This model is typically created by Data Architects and Business Analysts.
		 The purpose is to developed technical map of rules and data structures.
*/

/* PHYSICAL MODELING:
		
		 This Data Model describes HOW the system will be implemented using a specific DBMS system.
		 This model is typically created by DBA and developers.
		 The purpose is actual implementation of the database.
		 
*/

```



