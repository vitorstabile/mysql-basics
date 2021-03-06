# Content

1. [Chapter 1: MySQL](#chapter1)
    - [Chapter 1 - Part 1: Create User MySQL](#chapter1part1)
    - [Chapter 1 - Part 2: Login User MySQL](#chapter1part2)
    - [Chapter 1 - Part 3: Create Database MySQL](#chapter1part3)
    - [Chapter 1 - Part 4: Data Type MySQL](#chapter1part4)
    - [Chapter 1 - Part 5: Project Modeling MySQL](#chapter1part5)
    - [Chapter 1 - Part 6: Create Table MySQL](#chapter1part6)
    - [Chapter 1 - Part 7: Primary Key MySQL](#chapter1part7)
    - [Chapter 1 - Part 8: Foreign Key MySQL](#chapter1part8)
    - [Chapter 1 - Part 9: Alter Table MySQL](#chapter1part9)
    - [Chapter 1 - Part 10: Drop Table MySQL](#chapter1part10)
    - [Chapter 1 - Part 11: Insert MySQL](#chapter1part11)
    - [Chapter 1 - Part 12: Update MySQL](#chapter1part12)
    - [Chapter 1 - Part 13: Delete MySQL](#chapter1part13)
    - [Chapter 1 - Part 14: Tables Examples MySQL](#chapter1part14)
    - [Chapter 1 - Part 15: Select MySQL](#chapter1part15)
    - [Chapter 1 - Part 16: Or And MySQL](#chapter1part16)
    - [Chapter 1 - Part 17: In Exist Subquery MySQL](#chapter1part17)
    - [Chapter 1 - Part 18: As Aliases MySQL](#chapter1part18)
    - [Chapter 1 - Part 19: Join Table MySQL](#chapter1part19)
    - [Chapter 1 - Part 20: Order By MySQL](#chapter1part20)
    - [Chapter 1 - Part 21: Create Table with Select MySQL](#chapter1part21)
    - [Chapter 1 - Part 22: Insert Table with Select MySQL](#chapter1part22)
    - [Chapter 1 - Part 23: Alter Table with Select MySQL](#chapter1part23)
    - [Chapter 1 - Part 24: Delete Table with Select MySQL](#chapter1part24)
    - [Chapter 1 - Part 25: Aggregation Functions MySQL](#chapter1part25)
    - [Chapter 1 - Part 26: String Functions MySQL](#chapter1part26)
    - [Chapter 1 - Part 27: Arithmetic Functions MySQL](#chapter1part27)
    - [Chapter 1 - Part 28: Mathematical Operations MySQL](#chapter1part28)
    - [Chapter 1 - Part 29: Data Functions MySQL](#chapter1part29)
    - [Chapter 1 - Part 30: Stored Procedures MySQL](#chapter1part30)
    - [Chapter 1 - Part 31: Create Functions MySQL](#chapter1part31)
    - [Chapter 1 - Part 32: Event Scheduler MySQL](#chapter1part32)
    - [Chapter 1 - Part 33: Triggers MySQL](#chapter1part33)
    - [Chapter 1 - Part 34: Index MySQL](#chapter1part34)
    - [Chapter 1 - Part 35: Views MySQL](#chapter1part35)
    - [Chapter 1 - Part 36: Backups MySQL](#chapter1part36)
    - [Chapter 1 - Part 37: Export CSV MySQL](#chapter1part37)
    - [Chapter 1 - Part 38: Import CSV MySQL](#chapter1part38)


## <a name="chapter1"></a>Chapter 1: MySQL

#### <a name="chapter1part1"></a>Chapter 1 - Part 1: Create User MySQL

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

#### <a name="chapter1part10"></a>Chapter 1 - Part 10: Drop Table MySQL

```sql

/* Drop Table is use to delete a table */

drop table comvendas;

```

#### <a name="chapter1part11"></a>Chapter 1 - Part 11: Insert MySQL

```sql

/* Insert is used to insert values to a column in a specific table */ 

/* SQL form 1 (Caution with the sequence): insert into (table name) values (value1, value2, value3...); */

/* SQL form 2 (most used): insert into (table name) (column name1, column name2...) values (value1 for column name1, value2 for column name2...); */

/* SQL form 3 (Just MYSQL): insert into (table name) */
/*  values (value column name1, value column name2, value column name3...) */
/*  (value column name1, value column name2, value column name3...); */

/* Form 2 */
insert into comclien(n_numeclien,c_codiclien,c_nomeclien,c_razaclien,d_dataclien,c_cnpjclien,c_foneclien,c_cidaclien,c_estaclien) values (1,'0001','AARONSON','AARONSON FURNITURE LTDA','2015-02-17','17.807.928/0001-85','(21) 8167-6584','QUEIMADOS','RJ');

/* Form 1 */
insert into comclien values (2,'0001','AARONSON','AARONSON FURNITURE LTDA','2015-02-17','17.807.928/0001-85','(21) 8167-6584','QUEIMADOS','RJ');

```

#### <a name="chapter1part12"></a>Chapter 1 - Part 12: Update MySQL

```sql

/* Update clause is used to  alter values of a specific row in a column */

/* SQL: update (table name) set (column name) = (value) where (column name with especific value - common use is primary key); */

/* after the update, to save, you have to use the command commit */

/* SQL: commit; */

/* to dismiss the update, use the command rollback */

/* SQL: rollback; */

/*  Caution - Use the Where clause for every update and delete SQL command */

update comclien set c_nomeclien = 'AARONSON FURNITURE' where n_numeclien = 1;

commit;

update comclien set c_nomeclien = 'AARONSON FURNITURE', c_cidaclien = 'LONDRINA', c_estaclien = 'PR' where n_numeclien = 1;

commit;

update comclien set c_nomeclien = 'AARONSON' where n_numeclien = 1;

rollback;

```

#### <a name="chapter1part13"></a>Chapter 1 - Part 13: Delete MySQL

```sql

/* Delete clause is used to erase values form column. */

/* Is not like drop. Drop is used to erase objects from database, like tables, columns, views, procedures...*/

/* SQL: delete from (table name) where (column name with especific value - common use is primary key); */

/* after the delete, to save, you have to use the command commit */

/* SQL: commit; */

/* to dismiss the delete, use the command rollback */

/* SQL: rollback; */

/*  Caution - Use the Where clause for every update and delete SQL command */

delete from comclien where n_numeclien = 1;

commit;

delete from comclien;

commit;

```

#### <a name="chapter1part14"></a>Chapter 1 - Part 14: Tables Examples MySQL

```sql

/* https://github.com/viniciuscdes/mysqlbook/blob/master/popula_banco.sql */

/* create tables */

create table comclien(n_numeclien int not null auto_increment, c_codiclien varchar(10),c_nomeclien varchar(50),c_razaclien varchar(50),d_dataclien date,c_cnpjclien varchar(20),c_foneclien varchar(15),c_cidaclien varchar(50), c_estaclien varchar(100), primary key (n_numeclien));
 
create table comforne(n_numeforne int not null auto_increment,c_codiforne varchar(10),c_nomeforne varchar(50),c_razaforne varchar(50),c_foneforne varchar(15), primary key(n_numeforne));

create table comprodu(n_numeprodu int not null auto_increment,c_codiprodu varchar(20),c_descprodu varchar(100),n_valoprodu float(10,2),c_situprodu varchar(1),n_numeforne int,primary key(n_numeprodu)); 

create table comvenda(n_numevenda int not null auto_increment,c_codivenda varchar(10),n_numeclien int not null,n_numeforne int not null,n_numevende int,n_valovenda float(10,2),n_descvenda float(10,2),n_totavenda float(10,2),d_datavenda date, primary key(n_numevenda)); 

/* will be create a column n_vcomvenda FLOAT (10,2) further in comvenda table */

create table comvende(n_numevende int not null auto_increment,c_codivende varchar(10),c_nomevende varchar(50),c_razavende varchar(50),c_fonevende varchar(20),n_porcvende float(10,2),primary key(n_numevende));

create table comivenda(n_numeivenda int not null auto_increment,n_numevenda  int not null,n_numeprodu  int not null,n_valoivenda float(10,2),n_qtdeivenda int,n_descivenda float(10,2),primary key(n_numeivenda));

/* create foreign keys */ 

alter table comvenda add constraint fk_comprodu_comforne foreign key(n_numeforne) references comforne(n_numeforne) on delete no action on update no action;

alter table comvenda add constraint fk_comprodu_comvende foreign key(n_numevende) references comvende(n_numevende) on delete no action on update no action;

alter table comvenda add constraint fk_comvenda_comclien foreign key(n_numeclien) references comclien(n_numeclien) on delete no action on update no action;

alter table comivenda add constraint fk_comivenda_comprodu foreign key(n_numeprodu) references comprodu (n_numeprodu) on delete no action on update no action;

alter table comprodu add constraint fk_comprodu_comfornea foreign key(n_numeforne) references comforne (n_numeforne) on delete no action on update no action;

/* describe tables */

desc comclien;
desc comforne;
desc comprodu;
desc comvenda;
desc comvende;
desc comivenda;

/* client table example */

insert into comclien values(	1 	,'0001','AARONSON FURNITURE'   	    ,'AARONSON FURNITURE LTD'	,'2015-02-17 23:14:50',     '17.807.928/0001-85', '(21) 8167-6584' ,'QUEIMADOS'             ,'RJ' );
insert into comclien values(	2   ,'0002','LITTLER '             	    ,'LITTLER  LTDA'        	,'2015-02-17 23:14:50',     '55.643.605/0001-92', '(27) 7990-9502' ,'SERRA'                	,'ES' );
insert into comclien values(	3   ,'0003','KELSEY  NEIGHBOURHOOD'	    ,'KELSEY  NEIGHBOURHOOD' 	,'2015-02-17 23:14:50',     '05.202.361/0001-34', '(11) 4206-9703' ,'BRAGAN??A PAULISTA'    	,'SP' );
insert into comclien values(	4   ,'0004','GREAT AMERICAN MUSIC' 	    ,'GREAT AMERICAN MUSIC'	    ,'2015-02-17 23:14:50',     '11.880.735/0001-73', '(75) 7815-7801' ,'SANTO ANT??NIO DE JESUS','BA' );
insert into comclien values(	5   ,'0005','LIFE PLAN COUNSELLING'	    ,'LIFE PLAN COUNSELLING' 	,'2015-02-17 23:14:50',     '75.185.467/0001-52', '(17) 4038-9355' ,'BEBEDOURO'            	,'SP' );
insert into comclien values(	6   ,'0006','PRACTI-PLAN'          	    ,'PRACTI-PLAN LTDA'     	,'2015-02-17 23:14:50',     '32.518.106/0001-78', '(28) 2267-6159' ,'CACHOEIRO DE ITAPEMIRI','ES' );
insert into comclien values(	7   ,'0007','SPORTSWEST'           	    ,'SPORTSWEST LTDA'      	,'2015-02-17 23:14:50',     '83.175.645/0001-92', '(61) 4094-7184' ,'TAGUATINGA'           	,'DF' );
insert into comclien values(	8   ,'0008','HUGHES MARKETS'       	    ,'HUGHES MARKETS LTDA'  	,'2015-02-17 23:14:50',     '04.728.160/0001-02', '(21) 7984-9809' ,'RIO DE JANEIRO'       	,'RJ' );
insert into comclien values(	9   ,'0009','AUTO WORKS'           	    ,'AUTO WORKS LTDA'      	,'2015-02-17 23:14:50',     '08.271.985/0001-00', '(21) 8548-5555' ,'RIO DE JANEIRO'       	,'RJ' );
insert into comclien values( 10	,'00010','DAHLKEMPER ' ,'DAHLKEMPER  LTDA' ,'2015-02-17 23:14:50', '49.815.047/0001-00','(11) 4519-7670' ,'S??O PAULO' ,'SP' );

/* sellers table example */

insert into comvende values(1,'0001',    'CARLOS FERNANDES','CARLOS FERNANDES LTDA',  '(47) 7535-8144',12  );
insert into comvende values(2,'0002', 'J??LIA	GOMES', 'J??LIA GOMES LTDA', '(12) 8037-6661',25 );

/* providers table example */

insert into comforne values(1 ,'0001',  'DUN RITE LAWN MAINTENANCE'	   ,'DUN RITE LAWN MAINTENANCE LTDA'	,'(85) 7886-8837' );
insert into comforne values(2 ,'0002', 'SEWFRO FABRICS'	,'SEWFRO FABRICS LTDA'	,'(91) 5171-8483' );

/* product table example */

insert into comprodu values( 1	,	'123131',     'NOTEBOOK'	,'1251.29'  ,'A',	1  );
insert into comprodu values( 2	,	'123223',     'SMARTPHONE','1242.21'  ,'A',	2  );
insert into comprodu values( 3	,	'1231',     'DESKTOP'	,'1241.21'  ,'A',	1  );
insert into comprodu values( 4	,	'142123',     'TELEVIS??O'	,'2564.92'  ,'A',	2  );
insert into comprodu values( 5	, '7684', 'DRONE'	,'2325.32' ,'A', 1 ); 

/* order table example */

insert into comvenda values(1	    ,	'1'	    ,	1	,	1	,	1 ,  '25141.02'  ,	0	,	'25141.02'  ,  '2015-01-01'	 );
insert into comvenda values(2	    ,	'2'	    ,	2	,	2	,	2 ,  '12476.58'  ,	0	,	'12476.58'  ,  '2015-01-02'	 );
insert into comvenda values(3	    ,	'3'	    ,	3	,	1	,	1 ,  '16257.32'  ,	0	,	'16257.32'  ,  '2015-01-03'	 );
insert into comvenda values(4	    ,	'4'	    ,	4	,	2	,	2 ,  '8704.55',	    0	,	'8704.55'   ,  '2015-01-04'	 );
insert into comvenda values(5	    ,	'5'	    ,	5	,	1	,	1 ,  '13078.81',	0	,	'13078.81'  ,  '2015-01-01'	 );
insert into comvenda values(6	    ,	'6'	    ,	6	,	2	,	2 ,  '6079.19',	    0	,	'6079.19'   ,  '2015-01-02'	 );
insert into comvenda values(7	    ,	'7'	    ,	7	,	1	,	1 ,  '7451.26',	    0	,	'7451.26'   ,  '2015-01-03'	 );
insert into comvenda values(8	    ,	'8'	    ,	8	,	2	,	2 ,  '15380.47',	0	,	'15380.47'  ,  '2015-01-04'	 );
insert into comvenda values(9	    ,	'9'	    ,	9	,	1	,	1 ,  '13508.34',	0	,	'13508.34'  ,  '2015-01-01'	 );
insert into comvenda values(10	    ,	'10'	,	1	,	2	,	2 ,  '20315.07',	0	,	'20315.07'  ,  '2015-01-02'	 );
insert into comvenda values(11	    ,	'11'	,	1	,	1	,	1 ,  '8704.55',	    0	,	'8704.55'   ,  '2015-01-01'	 );
insert into comvenda values(12	    ,	'12'	,	2	,	2	,	2 ,  '11198.05',	0	,	'11198.05'  ,  '2015-01-02'	 );
insert into comvenda values(13	    ,	'13'	,	3	,	1	,	1 ,  '4967.84',	    0	,	'4967.84'   ,  '2015-01-03'	 );
insert into comvenda values(14	    ,	'14'	,	3	,	2	,	2 ,  '7451.26',	    0	,	'7451.26'   ,  '2015-01-04'	 );
insert into comvenda values(15	    ,	'15'	,	5	,	1	,	1 ,  '10747.359',	0	,	'10747.36'  ,  '2015-01-01'	 );
insert into comvenda values(16	    ,	'16'	,	6	,	2	,	2 ,  '13502.34',	0	,	'13502.34'  ,  '2015-01-02'	 );
insert into comvenda values(17	    ,	'17'	,	7	,	1	,	1 ,  '22222.99',	0	,	'22222.99'  ,  '2015-01-03'	 );
insert into comvenda values(18	    ,	'18'	,	8	,	2	,	2 ,  '15465.69',	0	,	'15465.69'  ,  '2015-01-04'	 );
insert into comvenda values(19	    ,	'19'	,	9	,	1	,	1 ,  '4650.64',	    0	,	'4650.64'   ,  '2015-01-01'	 );
insert into comvenda values(20	    ,   '20'	,   9	,   2	,   2 ,  '6975.96',     0	,   '6975.96'   ,  '2015-01-02'	);

/* order item example */

insert into comivenda values(1 ,1 ,1,'1251.29',1,0);
insert into comivenda values(2 ,1 ,2,'1242.21',2,0);
insert into comivenda values(3 ,1 ,3,'1241.21',3,0);
insert into comivenda values(4 ,1 ,4,'1513.77',4,0);
insert into comivenda values(5 ,1 ,5,'2325.32',5,0);               
insert into comivenda values(6 ,2 ,1,'1251.29',6,0);               
insert into comivenda values(7 ,3 ,3,'1241.21',7,0);               
insert into comivenda values(8 ,4 ,1,'1251.29',1,0);              
insert into comivenda values(9 ,5 ,3,'1241.21',2,0);              
insert into comivenda values(10,6 ,1,'1251.29',3,0);              
insert into comivenda values(11,7 ,2,'1242.21',4,0);
insert into comivenda values(12,8 ,5,'2325.32',5,0);
insert into comivenda values(13,9 ,2,'1242.21',6,0);
insert into comivenda values(14,10,3,'1241.21',7,0);
insert into comivenda values(15,11,1,'1251.29',1,0);
insert into comivenda values(16,12,1,'1251.29',2,0);
insert into comivenda values(17,13,2,'1242.21',3,0);
insert into comivenda values(18,14,2,'1242.21',4,0);
insert into comivenda values(19,15,3,'1241.21',5,0);
insert into comivenda values(20,16,3,'1241.21',6,0);
insert into comivenda values(21 ,17,4,'1513.77',7,0);
insert into comivenda values(22 ,18,4,'1513.77',1,0);
insert into comivenda values(23 ,19,5,'2325.32',2,0);
insert into comivenda values(24 ,20,5,'2325.32',3,0);
insert into comivenda values(25 ,2 ,2,'1242.21',4,0);
insert into comivenda values(26 ,3 ,4,'1513.77',5,0);
insert into comivenda values(27 ,4 ,2,'1242.21',6,0);
insert into comivenda values(28 ,5 ,4,'1513.77',7,0);
insert into comivenda values(29 ,6 ,5,'2325.32',1,0);
insert into comivenda values(30,7 ,3,'1241.21',2,0);
insert into comivenda values(31,8 ,1,'1251.29',3,0);
insert into comivenda values(32,9 ,4,'1513.77',4,0);
insert into comivenda values(33,10,5,'2325.32',5,0);
insert into comivenda values(34,11,2,'1242.21',6,0);
insert into comivenda values(35,12,2,'1242.21',7,0);
insert into comivenda values(36,13,3,'1241.21',1,0);
insert into comivenda values(37,14,3,'1241.21',2,0);
insert into comivenda values(38,15,4,'1513.77',3,0);
insert into comivenda values(39,16,4,'1513.77',4,0);
insert into comivenda values(40,17,5,'2325.32',5,0);
insert into comivenda values(41,18,5,'2325.32',6,0);

/* Verify all tables */

select * from comclien;
select * from comvenda;
select * from comvende;
select * from comivenda;
select * from comprodu;
select * from comforne; 

```

#### <a name="chapter1part15"></a>Chapter 1 - Part 15: Select MySQL

```sql

/* Select is a clause used to make a selection of what you want to see */

/* SQL: select (column name) from (table name); */

select * from comclien;

/* if you want to select multiples column */

select n_numeclien, c_codiclien, c_razaclien from comclien;

/* if you want to select a specify row */

select n_numeclien, c_codiclien, c_razaclien from comclien where c_codiclien = '0001';

/* if you want to select a specify row, but diferent from what have the where clause */

select n_numeclien, c_codiclien, c_razaclien from comclien where c_codiclien <> '0001';

/* We can use the operators >, <, >=, <=, for numeric types */

select n_numeclien, c_codiclien, c_razaclien from comclien where n_numeclien < 3;

select n_numeclien, c_codiclien, c_razaclien from comclien where n_numeclien > 3;

/* for strings, we can use the like clause with % */

select n_numeclien, c_codiclien, c_razaclien from comclien where c_razaclien like 'L%';

select n_numeclien, c_codiclien, c_razaclien from comclien where c_razaclien like '%LIT%';

select n_numeclien, c_codiclien, c_razaclien from comclien where c_razaclien like '%LTDA';

```

#### <a name="chapter1part16"></a>Chapter 1 - Part 16: Or And MySQL

```sql

/* Logical Operators */

/* OR -> For a true output, just one condition have to be true */

/* AND -> For a true output, all condition have to be true */

select n_numeclien, c_codiclien, c_razaclien from comclien where n_numeclien = 1 and c_razaclien like '%AARONSON%';
 
select n_numeclien, c_codiclien, c_razaclien from comclien where n_numeclien = 1 and c_razaclien = 'LITTLER  LTDA';

select n_numeclien, c_codiclien, c_razaclien from comclien where n_numeclien = 1 or c_razaclien = 'LITTLER  LTDA';

select n_numeclien, c_codiclien, c_razaclien from comclien where n_numeclien = 2 or c_razaclien = 'LITTLER  LTDA';

select n_numeclien, c_codiclien, c_razaclien from comclien where (n_numeclien = 2 or c_razaclien = 'AUTO WORKS LTDA') or (n_numeclien = 3 or c_razaclien = 'DAHLKEMPER  LTDA');

select n_numeclien, c_codiclien, c_razaclien from comclien where (n_numeclien = 2 or c_razaclien = 'AUTO WORKS LTDA') and (n_numeclien = 3 or c_razaclien = 'DAHLKEMPER  LTDA');

select n_numeclien, c_codiclien, c_razaclien from comclien where (n_numeclien = 2 and c_razaclien = 'LITTLER  LTDA') or (n_numeclien = 3 and c_razaclien = 'KELSEY  NEIGHBOURHOOD');

select n_numeclien, c_codiclien, c_razaclien from comclien where (n_numeclien = 2 and c_razaclien = 'LITTLER  LTDA') and (n_numeclien = 3 and c_razaclien = 'KELSEY  NEIGHBOURHOOD');

select n_numeclien, c_codiclien, c_razaclien from comclien where (n_numeclien = 2 or c_razaclien = 'AUTO WORKS LTDA') or (n_numeclien = 3 and c_razaclien = 'KELSEY  NEIGHBOURHOOD');

select n_numeclien, c_codiclien, c_razaclien from comclien where n_numeclien = 2 or (n_numeclien = 3 and c_razaclien = 'KELSEY  NEIGHBOURHOOD');

select n_numeclien, c_codiclien, c_razaclien from comclien where n_numeclien = 2 and (n_numeclien = 3 or c_razaclien = 'KELSEY  NEIGHBOURHOOD');

```

#### <a name="chapter1part17"></a>Chapter 1 - Part 17: In Exist Subquery MySQL

```sql

/* To make subquery's, we need to use the clauses in, not in, exists and not exists */

/* in and not in */

/* we want to  return two clients in a same query */

/* the query below gives a error */

select c_codiclien, c_razaclien from comclien where n_numeclien = 1,2;

/* To do this, we use the clause in or not in */

select c_codiclien, c_razaclien from comclien where n_numeclien in (1,2);

select c_codiclien, c_razaclien from comclien where n_numeclien not in (1,2);

/* we can make a subquery */

select c_razaclien from comclien where n_numeclien in (select n_numeclien from comvenda where n_numeclien);

select c_razaclien from comclien where n_numeclien not in (select n_numeclien from comvenda where n_numeclien);

/* Always compare primary key from one table to foreign key from the other table) */

select c_codivenda, (select c_razaclien from comclien where n_numeclien = comvenda.n_numeclien) from comvenda;

select n_numevenda, (select c_descprodu from comprodu where n_numeprodu = comivenda.n_numeprodu) from comivenda;

```

#### <a name="chapter1part18"></a>Chapter 1 - Part 18: As Aliases MySQL

```sql

/* To give a temporaly name for a column in a selec, we can use aliases with as clause*/

select c_codiclien as CODIGO, c_nomeclien as CLIENTE from comclien where n_numeclien not in(1,2,3,4);

select c_codivenda as Cod_Venda, (select c_razaclien from comclien where n_numeclien = comvenda.n_numeclien) as Nome_Cliente from comvenda;

```

#### <a name="chapter1part19"></a>Chapter 1 - Part 19: Join Table MySQL

```sql

/* If we want a report with two tables or more, we have to use the clause join */

/* For join clause with two or more tables, we need to use selection, projection and junction */

/* We need to see the relational diagram. In the example below, we will make a join table with the comvenda table */

/* this table have his own primary key n_numevenda and two other foreign key n_numeforne from comforne and n_numeclien from comclien */

/* Three table example */

select comvenda.n_numevenda, comvenda.n_valovenda, comforne.c_nomeforne, comclien.c_nomeclien /* projection - table comvenda - comforne and comclien */
from comvenda /*source table comvenda */
inner join comforne /* junction table comforne */
on comvenda.n_numeforne = comforne.n_numeforne
inner join comclien /* junction table comclien */
on comvenda.n_numeclien = comclien.n_numeclien;

/* Two table example */

select comvenda.n_numevenda, comvenda.n_valovenda, comforne.c_nomeforne /* projection - table comvenda - comforne */
from comvenda /*source table comvenda */
inner join comforne /* junction table comforne */
on comvenda.n_numeforne = comforne.n_numeforne;

```

#### <a name="chapter1part20"></a>Chapter 1 - Part 20: Order By MySQL

```sql

/* The order by is used to ordinate the select */

select comvenda.n_numevenda, comvenda.n_valovenda, comforne.c_nomeforne, comclien.c_nomeclien /* projection - table comvenda - comforne and comclien */
from comvenda /*source table comvenda */
inner join comforne /* junction table comforne */
on comvenda.n_numeforne = comforne.n_numeforne
inner join comclien /* junction table comclien */
on comvenda.n_numeclien = comclien.n_numeclien
order by c_nomeclien;

select comvenda.n_numevenda, comvenda.n_valovenda, comforne.c_nomeforne, comclien.c_nomeclien /* projection - table comvenda - comforne and comclien */
from comvenda /*source table comvenda */
inner join comforne /* junction table comforne */
on comvenda.n_numeforne = comforne.n_numeforne
inner join comclien /* junction table comclien */
on comvenda.n_numeclien = comclien.n_numeclien
order by n_numevenda;

select comvenda.n_numevenda, comvenda.n_valovenda, comforne.c_nomeforne, comclien.c_nomeclien /* projection - table comvenda - comforne and comclien */
from comvenda /*source table comvenda */
inner join comforne /* junction table comforne */
on comvenda.n_numeforne = comforne.n_numeforne
inner join comclien /* junction table comclien */
on comvenda.n_numeclien = comclien.n_numeclien
order by n_valovenda;

select comvenda.n_numevenda, comvenda.n_valovenda, comforne.c_nomeforne, comclien.c_nomeclien /* projection - table comvenda - comforne and comclien */
from comvenda /*source table comvenda */
inner join comforne /* junction table comforne */
on comvenda.n_numeforne = comforne.n_numeforne
inner join comclien /* junction table comclien */
on comvenda.n_numeclien = comclien.n_numeclien
order by c_nomeforne;

```

#### <a name="chapter1part21"></a>Chapter 1 - Part 21: Create Table with Select MySQL

```sql

/* We can create a table with the select clause */

/* QUERY: create table (table name) as (select (column name) from (table name)); */

create table comclien_bkp as (select * from comclien);

create table comclien_bkp2 as (select * from comclien where c_estaclien = 'SP');

select * from comclien_bkp;

select * from comclien_bkp2;

```

#### <a name="chapter1part22"></a>Chapter 1 - Part 22: Insert Table with Select MySQL

```sql

/* We can insert into atable with the select clause */

/* QUERY: insert into (table name) (select (column name) from (table name)); */

create table comcontato( n_numecontato int not null auto_increment, c_nomecontato varchar(200), c_fonecontato varchar(30), c_cidacontato varchar(200), c_estacontato varchar(2), n_numeclien int, primary key(n_numecontato));

insert into comcontato(select n_numeclien,c_nomeclien,c_foneclien,c_cidaclien,c_estaclien,n_numeclien from comclien);

select * from comcontato;

/* with multiple tables */

insert into comventp_teste (n_numeivenda, n_numeprodu,c_descprodu,n_valoivenda) select n_numeivenda,n_numeprodu,(select c_descprodu from comprodu where n_numeprodu = comivenda.n_numeprodu),n_valoivenda from comivenda;

```

#### <a name="chapter1part23"></a>Chapter 1 - Part 23: Alter Table with Select MySQL

```sql

/* We can alter a table with select */
 
 update comcontato set c_cidacontato = 'LONDRINA', c_estacontato = 'PR' where n_numeclien in ( select n_numeclien from comclien_bkp);

```

#### <a name="chapter1part24"></a>Chapter 1 - Part 24: Delete Table with Select MySQL

```sql

/* We can delete a table with select */
 
delete from comcontato where n_numeclien not in (select n_numeclien from comvenda );
 
commit;

```

#### <a name="chapter1part25"></a>Chapter 1 - Part 25: Aggregation Functions MySQL

```sql

/* The aggregation functions is responsible to group many values and return one value for a group */

/* Order By */

/* In this SQL function is gonna order by name in a select, but we have the repeated values */

select c_codiclien, c_razaclien 
from comvenda, comclien 
where comvenda.n_numeclien = comclien.n_numeclien 
order by c_razaclien;

/* Group by */

/* In this SQL function we don't have repeated values in a select */

select c_codiclien, c_razaclien
from comclien, comvenda
where comvenda.n_numeclien = comclien.n_numeclien
group by c_codiclien, c_razaclien
order by c_razaclien;

/* Count() */

/* In this SQL function, we can count the values from a select */

select c_codiclien, c_razaclien, count(n_numevenda) Qtde
from comclien, comvenda
where comvenda.n_numeclien = comclien.n_numeclien
group by c_codiclien, c_razaclien
order by c_razaclien;

/* We can count the datas from a table */

select count(*) from comclien;

/* Having count() */

/* This SQL function is use with count() function to specify a condition */

select c_razaclien, count(n_numevenda)
from comclien, comvenda
where comvenda.n_numeclien = comclien.n_numeclien
group by c_razaclien
having count(n_numevenda) > 2;

/* Max() and Min() */

/* This SQL function is to return the max or min value from a cloumn */

select max(n_totavenda) maior_venda from comvenda;

select min(n_totavenda) menor_venda from comvenda;

/* In the same time */

select min(n_totavenda) menor_venda, max(n_totavenda) maior_venda from comvenda;

/* Sum() */

/* This SQL function is use to sum values */

select sum(n_valovenda) valor_venda, 
	   sum(n_descvenda) descontos, 
	   sum(n_totavenda) total_venda
from comvenda
where d_datavenda between '2015-01-01' and '2015-01-31';

/* Avg() */

/* This SQL function is use to make average values from a column. We can put the float size */

select format(avg(n_totavenda),2) from comvenda;

```

#### <a name="chapter1part26"></a>Chapter 1 - Part 26: String Functions MySQL

```sql

/* String functions (characters) can be used to modify the data, with respect to the selected values, */
/*	but also in the way they are presented. Or yet, */
/*	modify them for validation. */

/* substr() */

/* In this SQL function, we put the name of the column and the position of what we want. */
/* After that, we put what we want */

/* length() */

/* In this SQL function, we count how much characters we want */

select c_codiprodu, c_descprodu from comprodu where substr(c_codiprodu,1,3) = '123' and length(c_codiprodu) > 4;

select substr(c_razaclien,1,5) Razao_Social, length(c_codiclien) Tamanho_Cod from comclien where n_numeclien = 1;

/* Concat() */

/* In this SQL function, we can concat two or more columns */

select concat(c_razaforne,' - fone: ', c_foneforne) from comforne order by c_razaforne;

/* concat_ws() */

/* In this SQL function, we can inform the separator */

select concat(c_codiclien,' ',c_razaclien, ' ', c_nomeclien) from comclien where c_razaclien like 'GREA%';

select concat_ws(';',c_codiclien, c_razaclien, c_nomeclien) from comclien where c_razaclien like 'GREA%';

/* Lcase() and lower() */

/* In this SQL function, we can lower letters */

select lcase(c_razaclien) from comclien;

/* Ucase() */

/* In this SQL function, we can large the letters */

select ucase('banco de dados mysql') from dual;

```

#### <a name="chapter1part27"></a>Chapter 1 - Part 27: Arithmetic Functions MySQL

```sql

/* Round() */

/* This SQL function is used to round values */

select round('213.142',2) from dual;

/* format() */

/* This SQL function is used to format and round values */

select format('21123.142',2) from dual;

/* truncate() */

/* This SQL function is used to truncate values */

select truncate(max(n_totavenda),0) maior_venda from comvenda;

/* Sqrt() */

/* This SQL function is used to square root of values */

select sqrt(4);

/* Pi, Sin, Cos and tan */

select pi();

select sin(pi());

select cos(pi());

select tan(pi()+1);

```

#### <a name="chapter1part28"></a>Chapter 1 - Part 28: Mathematical Operations MySQL

```sql

/*
* : multiplication;
/ : division;
+ : addition;
- : subtraction.
*/

/* to make operations, we have to use the select clause */

/* * : multiplication */

select (n_qtdeivenda * n_valoivenda) multiplica????o from comivenda where n_numeivenda = 4;

/* / : division */

select truncate((sum(n_valoivenda) / count(n_numeivenda)),2) divis??o from comivenda;

/* + : addition */

select (n_valoivenda + n_descivenda) adi????o from comivenda where n_numeivenda = 4;

/* - : subtraction */

select (n_valoivenda - n_descivenda) subtra????o from comivenda where n_numeivenda = 4;

```

#### <a name="chapter1part29"></a>Chapter 1 - Part 29: Data Functions MySQL

```sql

/* The Data Format for MySQL YYYY-MM-DD */

/* Curdate() */

/* Return the local date */

 select curdate();
 
 /* now() and sysdate() */

/* Return the hour and local date */

select now();

select sysdate();

/* curtime() */

/* Return just the hour local */

select curtime();

/* datediff() */

/* The difference btwen two dates */

select datediff('2015-02-01 23:59:59','2015-01-01');

/* date_add() */

/* Add a date */

select date_add('2013-01-01', interval 31 day);

/* dayname() */

/* return the name of the date */

select dayname('2015-01-01');

/* dayname() */

/* return the day of the month */

select dayofmonth('2015-01-01');

/* extract() */

/* extract a year of a date */

select extract(year from '2015-01-01');

/* last_day() */

/* extract the last day of a month */

select last_day('2015-02-01');

/* Format a date */

/* date_format() */

select date_format('2015-01-10',get_format(date,'EUR'));

select str_to_date('01.01.2015',get_format(date,'USA'));

```

#### <a name="chapter1part30"></a>Chapter 1 - Part 30: Stored Procedures MySQL

```sql

/* Stored Procedure */

/*This is a example of a stored procedure */
/* We gonna make another example more easy */

alter table comvenda add n_vcomvenda float(10,2);

/* Once the fields are generated, we will create our stored procedure
which should look for the percentage value of each seller,
perform the processing and then update the
commission value column in the sales table. */


/* We will use the procedure to make this update, because in
our scenario, we had already created the bank without those columns and the
our system is already in production, that is, we are assuming that there are
people using it */ 

/* The delimeter of the procedure. Normalym use $$ */

delimiter $$

create procedure processa_comissionamento(in data_inicial date,in data_final date, out total_processado int )
begin
	declare total_venda float(10,2) default 0;
	declare venda int default 0;
	declare vendedor int default 0;
	declare comissao float(10,2) default 0;
	declare valor_comissao float(10,2) default 0;
	declare aux int default 0;
	declare fimloop int default 0;
	
	/* cursor para buscar os registros a serem */
	/* processados entre a data inicial e data final */
	/* e valor total de venda ?? maior que zero */

	declare busca_pedido cursor for select n_numevenda, n_totavenda, n_numevende from comvenda
		    where d_datavenda between data_inicial
			and data_final
			and n_totavenda > 0 ;
			 
	/* Fa??o aqui um tratamento para o banco n??o */
	/* executar o loop quando ele terminar */
	/* evitando que retorne qualquer erro */
	declare continue handler for sqlstate '02000' set fimloop = 1;

	/* abro o cursor */
	open busca_pedido;
	
		/* inicio do loop */
		vendas: LOOP
		
		/* Aqui verifico se o loop terminou */
		/* e saio do loop */
		if fimloop = 1 then leave vendas;
		end if;
		
		/* recebo o resultado da consulta em cada vari??vel */
		fetch busca_pedido into venda, total_venda,vendedor;
		
		/* busco o valor do percentual de cada vendedor */
		select n_porcvende into comissao from comvende where n_numevende = vendedor;
		
		/* verifico se o percentual do vendedor ?? maior */
		/* que zero logo ap??s a condi????o deve ter o then */
		if (comissao > 0 ) then
			/* calculo o valor da comissao */
			set valor_comissao = ((total_venda * comissao) / 100);
			
			/* fa??o o update na tabela comvenda com o */
			/* valor da comiss??o */
			update comvenda set n_vcomvenda = valor_comissao where n_numevenda = venda;
			commit;
			
		/* verifico se o percentual do vendedor ?? igual */
        /* zero na regra do nosso sistema se o vendedor */
        /* tem 0 ele ganha 0 porcento de comiss??o */
		elseif (comissao = 0) then
		
			update comvenda set n_vcomvenda = 0 where n_numevenda = venda;
			commit;
		/* se ele n??o possuir registro no percentual de */
		/* comiss??o ele ir?? ganhar 1 de comiss??o */
		/* isso pela regra de neg??cio do nosso sistema */
		else
			set comissao = 1;
			set valor_comissao = ((total_venda * comissao) / 100);
			
			update comvenda set n_vcomvenda = valor_comissao where n_numevenda = venda;
			commit;
		/* fecho o if */
		end if;
		
		set comissao = 0;
		/*utilizo a vari??vel aux para contar a quantidade */
		set aux = aux +1 ;
	end loop vendas;
		/* atribuo o total de vendas para a vari??vel de */
		/* sa??da */
	set total_processado = aux;
	/* fecho o cursor */
	close busca_pedido;
	
	/*retorno o total de vendas processadas */
	
	end$$
	
delimiter ;

/* To use the procedure */

call processa_comissionamento('2015-01-01','2015-05-30' ,@a);
select @a;

select * from comvenda;

/* A more simple procedure */

create table comexample (n_numetotal int not null auto_increment, n_numevende int not null, n_valortotal float(10,2), primary key(n_numetotal));

alter table comexample add constraint fk_comexample_comvende
	foreign key(n_numevende)
		references comvende (n_numevende)
			on delete no action
			on update no action;

insert into comexample (n_numevende) select n_numevende from comvende;

/* we gonna calculate the total value from each vendor */

delimiter $$

create procedure total_value()
begin
	select comvende.n_numevende, sum(comvenda.n_vcomvenda)
	from comvenda
	inner join comvende
	on comvende.n_numevende = comvenda.n_numevende
	group by n_numevende;

	/* or */

	/* select n_numevende, sum(n_vcomvenda) from comvenda group by n_numevende; */
	
	end$$
delimeter ;

call total_value();

```

#### <a name="chapter1part31"></a>Chapter 1 - Part 31: Create Functions MySQL

```sql

/* With the procedures, we were able to carry out processing, and */
/* yet, if we want to, get some return. Functions are used */
/* specifically to return something. */

/* We can spend some parameter with the same type of declaration that we make in */
/* procedure and inform the type of return we will have. */

/* If you want to create something to get some feedback, I advise */
/* use of a function, because we can use them in the middle */
/* consultation, unlike the procedure, that we have to */
/* run with a specific command. */

/* Let's create a function to return the name of the client, according with the number of the client */

delimiter $$

create function rt_nome_cliente(vn_numeclien int)
	returns varchar(50) deterministic
	
	begin
	
		declare nome varchar(50);
		
		select c_nomeclien into nome from comclien where n_numeclien = vn_numeclien;
		
		return nome;
		
	end $$
	
delimiter ;

/* estou passando como par??metro o id do cliente igual a 1 */

select rt_nome_cliente(1);

/* we can use function with select */

/* irei retornar o c??digo da venda, nome do cliente e a */
/* data da venda ordenando pelo nome e em seguida pela data */

select c_codivenda, rt_nome_cliente(n_numeclien), d_datavenda from comvenda order by 2,3;

```

#### <a name="chapter1part32"></a>Chapter 1 - Part 32: Event Scheduler MySQL

```sql

/*
We created a procedure to do the processing of
commissions. However, performing this processing may result in a
very boring activity. We can schedule events to do so
automatically and periodically. For this, we use the event
scheduler.
*/

/* 
Let's program the procedure
processa_comissionamento to run once a week.
Therefore, we will use on schedule every 1 week, which will
run the first time on '2015-03-01' at 23:00 hours.
First, we must enable the event_scheduler in our
DBMS, because, by default, it is disabled. Open the prompt and
type the command:
*/

set global event_scheduler = on;

delimiter $$
create event processa_comissao
on schedule every 1 week starts '2015-03-01 23:38:00'
do
	begin
	call processa_comissionamento(current_date() - interval 7 day, current_date(), @a );
	end
$$
delimiter ;

/* disable event */

alter event processa_comissao_event disable;

/* enable event */

alter event processa_comissao_event enable;

```

#### <a name="chapter1part33"></a>Chapter 1 - Part 33: Trigger MySQL

```sql

/* We created a process to generate the commission, which can be */
/* executed manually or with scheduled events. */

/* However, the our system is not very large and does not have numerous */
/* number of records. We could then do this operation in */
/* real time, at the exact moment the sale is launched. */
/* We will achieve this through triggers. */

/* trigger is a set of operations that are performed */
/* automatically when a change is made to a record that */
/* is related to a table. It can be invoked before or */
/* after a change to an insert, update or delete, */
/* there can be up to 6 triggers per table. */

/* Trigger Structure */

DELIMITER $$  /* 1: we define the delimiter */

CREATE TRIGGER NAME /* 2: We created the trigger with create trigger and put a name for the trigger */
BEFORE/AFTER INSERT/DELETE/UPDATE ON TABLE_NAME /* 3: We define whether the trigger will be triggered Before or after an Insert or Delete or Update in the table */
FOR EACH ROW

BEGIN

	SQL_QUERY
	
END

$$

delimiter ;

/*BEFORE INSERT E BEFORE UPDATE TRIGGER */

/* How we want to perform the calculation */
/* of the commission automatically, we must create two triggers: one */
/* when you enter a new sale and another when the */
/* we update. We will use the before insert conditions */
/* before insertion) and before update. Beyond */
/* of these two, there are others that I will show in sequence. */

/* To carry out our operation, we must consult the percentage */
/* of the salesperson registration commission to generate the calculation. */
/* Putting into practice what we have already learned, we will create a */
/* function to have this percentage. */

delimiter $$

create function rt_percentual_comissao(vn_n_numevende int)
returns float deterministic
begin
	declare percentual_comissao float(10,2);
	
	select n_porcvende
		into percentual_comissao
		from convende
		where n_numevende = vn_n_numevende;
		
		return percentual_comissao;
		end;
$$
delimiter ;

/* Now let's go to the code to create the trigger before insertion. */
/* Note that I will use the same calculation that I used in procedure. */

delimiter $$

create trigger tri_vendas_bi
before insert on comvenda
for each row

begin
	declare percentual_comissao float(10,2);
	declare valor_comissao float(10,2);
	
	/*busco o percentual de comiss??o que o vendedor deve receber */
	
	select rt_percentual_comissao(new.n_numevende) into percentual_comissao;
	
	/* calculo comiss??o */
	
	set valor_comissao = ((new.n_totavenda * percentual_comissao) / 100);
	
	/* recebo no novo valor de comiss??o */
	
	set new.n_vcomvenda = valor_comissao;
	
end
$$
delimeter ;

/* Now, when you insert a new record in the table */
/* sales, the calculation of the seller's commission amount will be */
/* performed and the field will be filled. */

/* However, the total value of the sale can be changed and, in the event of */
/* insertion or withdrawal of an item from it, the amount of the commission to be */
/* paid to the seller will also change. So we must create more */
/* a trigger on the sales table to make an update */
/* that amount for when that happens. */

delimiter $$

create trigger tri_vendas_bu
before update on comvenda
for each row

begin

declare percentual_comissao float(10,2);
declare valor_comissao float(10,2);

/* No update, verifico se o valor total novo da venda */
/* ?? diferente do total anterior, pois se forem iguais, */
/* n??o h?? necessidade do c??lculo */

if (old.n_totavenda <> new.n_totavenda) then
	select rt_percentual_comissao(new.n_numevende) into percentual_comissao;
	
	/* c??lculo da comiss??o */
	
	set
	valor_comissao = ((new.n_totavenda * percentual_comissao) / 100);
	
	/* recebo no novo valor de comiss??o */
	
	set new.n_vcomvenda = valor_comissao;
	
end if
end
$$
delimiter ;

/*AFTER INSERT E AFTER UPDATE TRIGGER */

/* We made triggers to perform the calculation based on the value of */
/* sales amount. However, we are manually adding your items */
/* and entering in the field n_totavenda. This can cause */
/* error occurs, unlike when inserted from */
/* an application; however, we can make this calculation */
/* performed automatically using a trigger. */

/* This time, we will use the types after insert (after */
/* insert) and after update (after changing) in the table */
/* comivenda (items of sale), so that, after inserting the */
/* products, the value of your total is calculated and the field n_totavenda is updated. */

delimiter $$

create trigger tri_vendas_ai
after insert on comivenda
for each row
begin

/* declaro as vari??veis que utilizarei */

	declare vtotal_itens float(10,2) default 0;
	declare total_item float(10,2) default 0;
	declare fimLoop boolean default false;
	
	/* cursor para buscar os itens j?? registrados da venda */
	declare busca_itens cursor for
		select n_valoivenda from comivenda where n_numevenda = new.n_numevenda;
		
	/*Handler para encerrar o loop antes da ??ltima linha */
	
	declare continue handler for sqlstate '02000' set fimLoop = true;
	
	/*abro o cursor */
	open busca_itens;
	/* declaro e inicio o loop */
	itens : loop fetch busca_itens into total_item;
	
	/* encerra o bloco quando o cursor n??o retornar mais linhas */
	
	if fimLoop then
		leave itens;
	end if;
	
	/* somo o valor total dos itens(produtos) */
	set vtotal_itens = vtotal_itens + total_item;
	
end loop itens;

close busca_itens;

/* atualizo o total da venda */
update comvenda set n_totavenda = vtotal_itens where n_numevenda = new.n_numevenda;

end
$$
delimiter ;

/* Agora temos a mesma situa????o que t??nhamos anteriormente,
pois a tabela de itens da venda pode ser atualizada e, se isso
ocorrer, o valor de seu total ficar?? incorreto. Por isso, devemos
criar uma trigger que o atualizar?? se o valor do item for alterado;
mas somente na condi????o de o novo ser diferente do antigo. Esse
n??o sendo o caso, n??o ?? necess??rio executar os c??lculos.
*/

delimiter $$
create trigger tri_ivendas_au
after update on comivenda
for each row
begin

/* declaro as vari??veis que utilizarei */

declare vtotal_itens float(10,2) default 0;
declare total_item float(10,2) default 0;
declare fimLoop boolean default false;

/* cursor para buscar os itens j?? registrados da venda */

declare busca_itens cursor for select n_valoivenda from comivenda where n_numevenda = new.n_numevenda;

/* Handler para encerrar o loop antes da ??ltima linha */

declare continue handler for sqlstate '02000' set fimLoop = true;

/* verifico se h?? necessidade de altera????o */
/* fa??o somente se o novo valor for alterado */

if new.n_valoivenda <> old.n_valoivenda then

/* abro o cursor */
open busca_itens;
/* declaro e inicio o loop */

itens : loop

fetch busca_itens into total_item;

/*encerra o bloco quando o cursor n??o retornar mais linhas */

	if fimLoop then
		leave itens;
	end if;
	
	/* somo o valor total dos itens(produtos) */
	
	set vtotal_itens = vtotal_itens + total_item;

end loop itens;

close busca_itens;

/* atualizo o total da venda */

update comvenda set n_totavenda = vtotal_itens where n_numevenda = new.n_numevenda;

end if;
end
$$
delimeter ;

/*BEFORE DELETE E AFTER DELETE TRIGGER */

/*
Now, you may have the following question: what if we
we delete an item from a sale? Really, if that happens
at this time, your total amount will be incorrect, as we have
just the triggers for insert and update. To correct this
problem, let's create one for the delete as well.
*/

delimiter $$
create trigger tri_ivendas_af
after delete on comivenda
for each row
begin
/* declaro as vari??veis que utilizarei */
declare vtotal_itens float(10,2) default 0;
declare total_item float(10,2) default 0;
declare fimLoop boolean default false;
/* cursor para buscar os itens j?? registrados da venda */

declare busca_itens cursor for
select n_valoivenda
from comivenda
where n_numevenda = old.n_numevenda;

/*Handler para encerrar o loop antes da ??ltima linha */
declare continue handler for
sqlstate '02000'
set fimLoop = true;
/* abro o cursor */
open busca_itens;
/* declaro e inicio o loop */
itens : loop

fetch busca_itens into total_item;

/*encerra o bloco quando o cursor n??o retornar mais linhas.*/

if fimLoop then
leave itens;
end if;
## somo o valor total dos itens(produtos)
set vtotal_itens = vtotal_itens + total_item;
end loop itens;
close busca_itens;
## atualizo o total da venda
update comvenda set n_totavenda = vtotal_itens
where n_numevenda = old.n_numevenda;
end
$$
delimiter ;

/*
We have one more situation that we can resolve using the
trigger: on delete. Remember the integrity issues of data.
 A table that has a foreign key cannot be deleted
a record without first deleting the primary record.
*/

delimiter $$
create trigger tri_vendas_bf
before delete on comvenda
for each row
begin
/* declaro as vari??veis que utilizarei /*
declare vtotal_itens float(10,2) default 0;
declare total_item float(10,2) default 0;
declare fimLoop boolean default false;
/* verifico se h?? necessidade de altera????o */
/* fa??o somente se o novo valor for alterado */
/* cursor para buscar os itens j?? registrados da venda */

declare busca_itens cursor for
select n_valoivenda
from comivenda
where n_numevenda = old.n_numevenda;

/*Handler para encerrar o loop antes da ??ltima linha */

declare continue handler for
sqlstate '02000'
set fimLoop = true;

/* abro o cursor */
open busca_itens;
/* declaro e inicio o loop */
itens : loop

fetch busca_itens into total_item;

/*encerra o bloco quando o cursor n??o retornar mais linhas */

if fimLoop then
leave itens;
end if;

/* somo o valor total dos itens(produtos) */

set vtotal_itens = vtotal_itens + total_item;

end loop itens;

close busca_itens;

/* atualizo o total da venda */

delete from comivenda where n_numevenda = old.n_numevenda;
end
$$
delimiter ;

/* TRIGGER STATUS */

/* to disable trigger */

alter trigger tri_vendas_bi desable;

/* to enable trigger */

alter trigger tri_vendas_bi enable;

/* to drop trigger */

drop trigger tri_vendas_bi;

```

#### <a name="chapter1part34"></a>Chapter 1 - Part 34: Index MySQL

```sql

/*
In order to assist in improving queries, MySQL
provides us indexes. When we create as our own
tables, we have already created a primary key index (primary key).
However, it is not used to make this optimization of
performance, as it only serves to take care of the integrity of data.
The initial measure we should take to improve the time
of queries is the creation of indexes for the tables
But what happens to this performance gain? When a table has no indexes, its records are
disorderly and a consultation will have to go through them all. If
if we add an index, a new table is generated. The amount
records of this new one is the same as the original one, the difference is
that they are organized.
/*
/* Create Index in a new table */

create table t1(
c1 int not null auto_increment,
c2 varchar(10),
c3 varchar(200),
c4 varchar(200),
c5 date,
c6 varchar(15),
c7 varchar(15),
primary key (c1),
index idx_t1(c2));

/* Create Index in a existing table */

alter table comclien add index idx_comclien_3(c_razaclien);

alter table comclien add index idx_comclien_4(c_codiclien);

show indexes from comclien;

/* When use */

/*
You should give preference to columns that we use to
search, ordering or grouping, in clauses: where,
joins, order by or group by.
*/

/* Won't use */

/*
f a column contains very different values ??????(for example,
the one that keeps the ages), an index will differentiate the records
quickly. However, it will not help with one that is used to
store gender (sex) records and contains only the values
M or F.
*/

/* Unique Index */

/*
MySQL also has other types of indexes. Another more
common is the unique index. As the name says, it is an index
that also serves to restrict duplication of data. To
create it in a column, you're telling the DBMS that it doesn't
can accept duplicate records there.
*/

alter table comvenda add unique index idx_comvenda_1(c_codivenda);

show indexes from comvenda;

```

#### <a name="chapter1part35"></a>Chapter 1 - Part 35: Views MySQL

```sql

/* 
We also know that every time we rewrite the same
consultation, we will achieve the same results as before. 
That is a serious task, as there are several ways to write a
same consultation. To alleviate this situation and also thinking
in performance and time saved, we can quickly transform these queries into a view. 
From that, she will remain stored on the database server at
form of a table so that we can consult it every time
we need, without having to rewrite it
A view is an object that belongs to a database,
defined and based on selects statements, returning a
given view of data from one or more tables. Those
objects are sometimes called virtual tables, formed from
other tables that, in turn, are called based tables or other Views. 
In some cases, these are upgradeable and can be insert, update and
delete, which actually modifies your based tables.
*/

/* Create View */

create or replace view clientes_vendas_fornecedor as
select comvenda.n_numevenda, comvenda.n_valovenda, comforne.c_nomeforne, comclien.c_nomeclien /* projection - table comvenda - comforne and comclien */
from comvenda
inner join comforne
on comvenda.n_numeforne = comforne.n_numeforne
inner join comclien
on comvenda.n_numeclien = comclien.n_numeclien;

select * from clientes_vendas_fornecedor;

/* Update views */

/* 
For you to be able to insert, update and delete a record
through a view, it cannot have joins and functions
aggregators, such as group by.
*/

create or replace view produtos as
select n_numeprodu,
c_codiprodu,
c_descprodu,
n_valoprodu,
c_situprodu,
n_numeforne
from comprodu;

insert into produtos values (6,'0006','SMART WATCH','2412.98','A',1);

update produtos set n_valoprodu = '1245.99' where n_numeprodu = 6;

```

#### <a name="chapter1part36"></a>Chapter 1 - Part 36: Backups MySQL

```sql

/* Create Backups Online */

/* With cmd, navegate to bin folder */

C:\Program Files\MySQL\MySQL Server 8.0\bin

/* Use this command to backup the database */

mysqldump -u root -p example > C:\Users\solun\Desktop\examplebackup.sql

/* To export trigger, functions and procedures */

mysqldump -u root -p --routines --triggers example > C:\Users\solun\Desktop\examplebackup.sql

/* Especific table */

mysqldump -u root -p example comclien > C:\Users\solun\Desktop\examplebackup.sql

/* All Databases */

mysqldump -u root -p --all-databases > C:\Users\solun\Desktop\examplebackup.sql

/* Import backup */

create database example2;

/* With cmd, navegate to bin folder */

C:\Program Files\MySQL\MySQL Server 8.0\bin

/* Make a back up */

mysqldump -u root -p --routines --triggers example > C:\Users\solun\Desktop\examplebackup.sql

/* In the same cmd, make */

mysql -h localhost -u root -p example2 < C:\Users\solun\Desktop\examplebackup.sql

use example2;

show tables;

```

#### <a name="chapter1part37"></a>Chapter 1 - Part 37: Export CSV MySQL

```sql

/* 
We can export to .csv file or .txt file
*/

/* First, you need to know where the file will be stored */

/* First, run this command to know the path */

SHOW VARIABLES LIKE "secure_file_priv";

/*
+------------------+------------------------------------------------+
| Variable_name    | Value                                          |
+------------------+------------------------------------------------+
| secure_file_priv | C:\ProgramData\MySQL\MySQL Server 8.0\Uploads\ |
+------------------+------------------------------------------------+
*/

/* Will be stored in C:\ProgramData\MySQL\MySQL Server 8.0\Uploads\ */

use example

/*
For example, let's save all the records in the
customers in a .txt file. On export, we will tell the
DBMS that we want to save the file to the c: / drive with the
example.txt. We want to separate each record
',' and limit each column with ''''.
*/

select * from comclien
into outfile 'C:\\ProgramData\\MySQL\\MySQL Server 8.0\\Uploads\\examplebackup1.txt'
fields terminated by ','
enclosed by '''';

select * from comclien
into outfile 'C:\\ProgramData\\MySQL\\MySQL Server 8.0\\Uploads\\examplebackup1.csv'
fields terminated by ','
enclosed by '''';

/* Another example */

SELECT * FROM calculo_receita.ingrediente 
INTO OUTFILE 'C:\\Temp\\teste.csv'
FIELDS ENCLOSED BY '"' 
TERMINATED BY ';' 
ESCAPED BY '"' 
LINES TERMINATED BY '\r\n';

```

#### <a name="chapter1part38"></a>Chapter 1 - Part 38: Import CSV MySQL

```sql

/* 
We can import to .csv file or .txt file
*/

/* First, you need to know where the file will be stored */

/* First, run this command to know the path */

SHOW VARIABLES LIKE "secure_file_priv";

/*
+------------------+------------------------------------------------+
| Variable_name    | Value                                          |
+------------------+------------------------------------------------+
| secure_file_priv | C:\ProgramData\MySQL\MySQL Server 8.0\Uploads\ |
+------------------+------------------------------------------------+
*/

/* Will be stored in C:\ProgramData\MySQL\MySQL Server 8.0\Uploads\ */

/*
The import via file can be very useful in actions of
popular data in a database or import it from others
systems or banks, as I described earlier. Of the same
way that export, it will not depend on an application or
of a tool.
*/

create table comuser(n_numeuser int not null auto_increment,n_nomeuser varchar(100),n_nascuser date,primary key(n_numeuser));

load data infile 'C:\\ProgramData\\MySQL\\MySQL Server 8.0\\Uploads\\example5.txt'
into table comuser
fields terminated by ','
lines terminated by '\n';

/* export */

select * from comuser
into outfile 'C:\\ProgramData\\MySQL\\MySQL Server 8.0\\Uploads\\example6.txt'
fields terminated by ','
enclosed by '''';

/* Another example */

SET GLOBAL local_infile = 1;

LOAD DATA LOCAL INFILE 'C:\\Users\\vep08.FESTPANDOMAIN\\Desktop\\Teste.csv'
INTO TABLE calculo_receita.ingrediente
CHARACTER SET latin1
FIELDS TERMINATED BY ';'
LINES TERMINATED BY '\n'
(id, codigo, descricao, custo);

SELECT * FROM calculo_receita.ingrediente;

```
