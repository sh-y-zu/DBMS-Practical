# MySQL Database Setup Instructions

## SQLCode_1.txt

1. Create a text file named "SQLCode_1.txt".
2. Open the text file with Notepad or any other text editor.
3. Type the following commands in the text file:

```sql
DROP DATABASE EMPLOYEE;
CREATE DATABASE EMPLOYEE;
USE EMPLOYEE;
TEE D:\DBMS Practical\Session4.txt
```

4. Save the text file.
5. Open the Command Prompt.
6. Log in to the MySQL server.
7. Type source followed by the path to the text file SQLCode_1.txt.
   
Example:

```
source D:\DBMSPractical\SQLCode_1.txt
```

## SQLCode_2.txt

9. Create another text file named "SQLCode_2.txt".
10. Open the text file with Notepad or any other text editor.
11. Type the following commands in the text file:

```
CREATE TABLE EMPLOYEE(
Fname VARCHAR(15) NOT NULL,
Minit CHAR,
Lname VARCHAR(15) NOT NULL,
SSN CHAR(9) NOT NULL,
Bdate DATE,
Address VARCHAR(30) DEFAULT 'Colombo',
Sex CHAR,
Salary DECIMAL(10,2),
Dno INT NOT NULL
);

CREATE TABLE DEPARTMENT (
Dname VARCHAR(15) NOT NULL,
Dnumber INT NOT NULL,
ManagerSSN CHAR(9) NOT NULL
);

ALTER TABLE EMPLOYEE
ADD CONSTRAINT PK PRIMARY KEY (SSN),
ADD CONSTRAINT FK_Dept FOREIGN KEY (Dno) REFERENCES DEPARTMENT (Dnumber);

ALTER TABLE DEPARTMENT
ADD CONSTRAINT PK PRIMARY KEY (Dnumber),
ADD CONSTRAINT FK_Emp FOREIGN KEY (ManagerSSN) REFERENCES EMPLOYEE (SSN);
```

12. Save the text file.
13. Type `source` followed by the path to the text file SQLCode_2.txt.
14. Check the results after execution.
