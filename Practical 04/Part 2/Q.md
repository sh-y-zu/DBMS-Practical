# Database Management System Exercise

## Description

This exercise involves creating tables based on a relational schema, inserting data into these tables using text files, and uploading data into the tables using the LOAD command. Below are the tasks to be performed:

1. Consider the following relational schema:
   - Supplier (Sno, Sname, status, city)
   - Parts (Pno, Pname, color, weight, city)
   - Supply (Sno, Pno, quantity)

2. Create the tables by applying appropriate constraints.

3. Save three text files to insert data into each table separately. Each piece of data should be separated by a comma. An example dataset is provided below:
   
   ```
   "100", "Steven", "King", "1993-06-07", "Programmer", 40000, 10
   "101", "Neena", "Kochchar", "1994-06-20", "Salesman", 60000, 20
   "102", "Lex", "Hunold", "1993-06-10", "Manager", 60000, 10
   "103", "Alexander", "Ernst", "2000-08-20", "Salesman", NULL, 20
   ```

4. Upload data from a text file to the tables using the LOAD command with the following format:
   
   ```
   LOAD DATA LOCAL INFILE "textfilepath/textfilename.txt"
   INTO TABLE tablename
   FIELDS TERMINATED BY ','
   OPTIONALLY ENCLOSED BY '"'
   LINES TERMINATED BY '\r\n';
   ```

5. Tables are provided below:

Supplier
| Sno | Sname  | Status | City    |
|-----|--------|--------|---------|
| S1  | Smith  | 20     | London  |
| S2  | Jones  | 10     | Paris   |
| S3  | Black  | 30     | Paris   |
| S4  | Clark  | 20     | London  |
| S5  | Adams  | 30     | Athens  |

Parts
| Pno | Pname | Color | Weight | City    |
|-----|-------|-------|--------|---------|
| 1   | Nut   | Red   | 12     | London  |
| 2   | Bolt  | Green | 17     | Paris   |
| 3   | Screw | Blue  | 17     | Rome    |
| 4   | Screw | Red   | 14     | London  |
| 5   | Cam   | Blue  | 12     | Paris   |
| 6   | Cog   | Red   | 19     | London  |

Supply
| Sno | Pno | Quantity |
|-----|-----|----------|
| S1  | P1  | 300      |
| S1  | P2  | 200      |
| S1  | P3  | 400      |
| S1  | P4  | 200      |
| S1  | P5  | 100      |
| S1  | P6  | 100      |
| S2  | P1  | 300      |
| S2  | P2  | 400      |
| S3  | P2  | 200      |
| S4  | P2  | 200      |
| S4  | P4  | 300      |
| S4  | P5  | 400      |


This README file outlines the tasks to be performed and provides necessary information regarding the database schema and data files for the exercise.
