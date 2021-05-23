# Content

1. [Chapter 1: MySQL](#chapter1)
    - [Chapter 1 - Part 1: Create User](#chapter1part1)
    - [Chapter 1 - Part 2: Login User MySQL](#chapter1part2)
    - [Chapter 1 - Part 3: Create Database MySQL](#chapter1part3)
    - [Chapter 1 - Part 4: Data Type MySQL](#chapter1part4)
    - [Chapter 1 - Part 5: Project Modeling MySQL](#chapter1part5)
    - [Chapter 1 - Part 6: Create Table MySQL](#chapter1part6)
    - [Chapter 1 - Part 7: Primary Key MySQL](#chapter1part7)
    - [Chapter 1 - Part 8: Foreign Key MySQL](#chapter1part8)
    - [Chapter 1 - Part 9: Alter Table MySQL](#chapter1part9)
    - [Chapter 1 - Part 10: Drop Table MySQL](#chapter1part10)

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

#### <a name="chapter1part6"></a>Chapter 1 - Part 6: Create Table MySQL

```sql


/* Create Table SQL - QUERY: CREATE TABLE (TABLE NAME)((COLUMN NAME 1)(DATA TYPE), (COLUMN NAME 2)(DATA TYPE), (COLUMN NAME n)(DATA TYPE)); */

create table comclien(n_numeclien int not null auto_increment, c_codiclien varchar(10),c_nomeclien varchar(50),c_razaclien varchar(50),d_dataclien date,c_cnpjclien varchar(20),c_foneclien varchar(15),primary key (n_numeclien));
 
create table comforne(n_numeforne int not null auto_increment,c_codiforne varchar(10),c_nomeforne varchar(50),c_razaforne varchar(50),c_foneforne varchar(15), primary key(n_numeforne));

create table comprodu(n_numeprodu int not null auto_increment,c_codiprodu varchar(20),c_descprodu varchar(100),n_valoprodu float(10,2),c_situprodu varchar(1),n_numeforne int,primary key(n_numeprodu)); 

create table comvenda(n_numevenda int not null auto_increment,c_codivenda varchar(10),n_numeclien int not null,n_numeforne int not null,n_numevende int not null,n_valovenda float(10,2),n_descvenda float(10,2),n_totavenda float(10,2),d_datavenda date,primary key(n_numevenda)); 

create table comvende(n_numevende int not null auto_increment,c_codivende varchar(10),c_nomevende varchar(50),c_razavende varchar(50),c_fonevende varchar(20),n_porcvende float(10,2),primary key(n_numevende));

create table comivenda(n_numeivenda int not null auto_increment,n_numevenda  int not null,n_numeprodu  int not null,n_valoivenda float(10,2),n_qtdeivenda int,n_descivenda float(10,2),primary key(n_numeivenda));

create table comvendas(n_numevenda int not null auto_increment,c_codivenda varchar(10),n_numeclien int not null,n_numeforne int not null,n_numevende int not null,n_valovenda float(10,2),n_descvenda float(10,2),n_totavenda float(10,2),d_datavenda date,primary key(n_numevenda)); /* tabela gerada errada para didatica */

/* To see all tables created - QUERY: show tables; */

show tables;

/* To describe a table - QUERY: desc (TABLE NAME); */

desc comclien;

/* The primary key clause is what makes the line or record a unique table. */

/* The auto_increment clause is used to increment automatically the primary key value of the table. */

/* The not null clause is used to a argument not be null when he is create */

```

#### <a name="chapter1part7"></a>Chapter 1 - Part 7: Primary Key MySQL

```sql


/* The Primary Key:
create table comclien(n_numeclien int not null auto_increment,
					c_codiclien varchar(10),
					c_nomeclien varchar(50),
					c_razaclien varchar(50),
					d_dataclien date,
					c_cnpjclien varchar(20),
					c_foneclien varchar(15),
					primary key (n_numeclien));
The primary key is what makes the line or record a
unique table. Originated, an automatic sequence is extracted
for the generation of this key so that it will not be repeated. In
our case, the n_numeclien will be unique, that is, no pair of
rows have the same value in the same column. It will be a
numeric preference string that identifies a record.
In the MySQL, to make a column a primary key:
create table (table name)((column name 1)(data type) not null auto_increment,
						  (column name 2)(data type),
						  (column name 3)(data type),
						   ....
						   ....
						   primary key (column name 1)); 
*/

```

#### <a name="chapter1part8"></a>Chapter 1 - Part 8: Foreign Key MySQL

```sql

  
/* The Foreign Key:
The foreign key defines a relationship between tables,
commonly called referential integrity. This rule is based
in the fact that a foreign key in a table is the key
primary in another.
When we created the comvenda table, we included columns of
other tables, such as n_numeclien, n_numeforne and
n_numeprodu. These columns are referencing a record in
your source table. However, as we only created the field, but
nothing that informs the bank about this reference, we should do
this, passing an instruction to our DBMS through the
constraints, as the codes show in the sequence.
To create and reference foreign keys, use the commands
- QUERY: alter table (table name) add constraint (name of the constraint)
		 foreign key (the column of the foreign key in the current table)
			references (table name reference of the foreign key)(the column of the primary key table reference)
				on delete no action
				on update no action;
				
*/
				
alter table comvenda add constraint fk_comprodu_comforne
	foreign key(n_numeforne)
		references comforne(n_numeforne)
			on delete no action
			on update no action;
			
alter table comvenda add constraint fk_comprodu_comvende
	foreign key(n_numevende)
		references comvende(n_numevende)
			on delete no action
			on update no action;
			
alter table comvenda add constraint fk_comvenda_comclien
	foreign key(n_numeclien)
		references comclien(n_numeclien)
			on delete no action
			on update no action;
			
alter table comivenda add constraint fk_comivenda_comprodu
	foreign key(n_numeprodu)
		references comprodu (n_numeprodu)
			on delete no action
			on update no action;
			
alter table comivenda add constraint fk_comivenda_comvenda
	foreign key(n_numevenda)
		references comvenda (n_numevenda)
			on delete no action
			on update no action;
			
/* To show all constrains */

/* - QUERY:	select * from information_schema.table_constraints where constraint_schema = 'YOUR_DATABASE_NAME'; */

select * from information_schema.table_constraints where constraint_schema = 'example';

```

#### <a name="chapter1part9"></a>Chapter 1 - Part 9: Alter Table MySQL

```sql


/* Alter Table is use to alter the type of the field */

/* SQL: alter table (table name) (add or drop) column (column name) (data type) */

/* 
	add - add table
	drop - Delete table
*/

alter table comclien add column c_cidaclien varchar(50);

alter table comclien drop column c_estclien;

alter table comclien add column c_estaclien varchar(50);

/* You can use with the modify clause to alter the data type without add or drop column */

alter table comclien modify column c_estaclien int;

alter table comclien modify column c_estaclien varchar(100);

```

#### <a name="chapter1part9"></a>Chapter 1 - Part 10: Drop Table MySQL

```sql

/* Drop Table is use to delete a table */

drop table comvendas;

```
