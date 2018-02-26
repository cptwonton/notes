## Oracle Database 11g SQL

#### Intro

###### What is a relational DB?
- Dr. E.F Codd came up with this concept back in 1970
- collection of related information organized into tables
- stores data in rows
- data arranged by columns
- tables stored in a schema
- can grant permissions to other users
- data stored is different from software (DBMS) used to access data
- DBMS examples:
  - Oracle
  - SQL Server
  - DB2
  - MySQL
- all use SQL (S-Q-L is official way to pronounce)

###### SQL
- developed by IBM, called System R
- Relational Software Inc., now known as Oracle, released first commercial version of SQL
- fully standardized now
- 5 types of statements:
  - Query retrieves rows stored in tables. Uses `SELECT` statement
  - DML statements modify contents of tables
    - `INSERT`
    - `UPDATE`
    - `DELETE`
  - DDL statements define data structures (like tables) that make up the database
    - `CREATE` creates a database structure, like `CREATE TABLE` or `CREATE USER`
    - `ALTER` modifies a database structure, like `ALTER TABLE`
    - `DROP` removes a database structure, like `DROP TABLE`
    - `RENAME` changes the name of a database structure
    - `TRUNCATE` removes all the rows from a table
  - Transaction Control (TC) statements permanently record changes made to rows, or undo the changes
    - `COMMIT` permanently records changes made to rows
    - `ROLLBACK` undoes changes made to rows
    - `SAVEPOINT` sets a save point to which you can roll back
  - DCL (Data Control Language) change permissions on database structures
    - `GRANT` gives another user access to database structures
    - `REVOKE` prevents another user from accessing database structures
   
###### SQL\*PLUS
- `SELECT SYSDATE from dual;`
  - `dual` is a generic table with a single row, can be used to eval. expressions, or get the date
  - `SYSDATE` is a built-in database function
  - modify previous command with `edit`
  - re-execute by typing `/`
  
###### SQL DEVELOPER
- can also use SQL Developer as alternative to SQL\*PLUS
- requires Java

###### SQL\*PLUS extras
- within SQL\*PLUS, run a script by `@ <path to the script>`
- to exit SQL\*PLUS, `EXIT`
` to disconnect/reconnect, `DISCONNECT` and `CONNECT`. this keeps SQL\*PLUS running

###### Creating a DB user
- `CREATE USER <username> IDENTIFIED BY <password>;`
  - this only creates the user, does not give permissions so user is kinda useless at this point
- `GRANT connect, resource TO store;`
  - connect privilege allows user to log into the DB
  - resource privilege allows user to create items like db tables


  
  
