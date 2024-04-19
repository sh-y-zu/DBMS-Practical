### Database Management System Exercise

#### 1. Schema Definition:

Consider the following relational schema:

- Supplier (Sno, Sname, status, city)
- Parts (Pno, Pname, color, weight, city)
- Supply (Sno, Pno, quantity)

#### 2. Table Creation:

Tables are created with appropriate constraints as follows:

Supplier:
```sql
CREATE TABLE Supplier (
    Sno VARCHAR(10) PRIMARY KEY,
    Sname VARCHAR(255),
    Status INT,
    City VARCHAR(255)
);

CREATE TABLE Parts (
    Pno VARCHAR(10) PRIMARY KEY,
    Pname VARCHAR(255),
    Color VARCHAR(255),
    Weight INT,
    City VARCHAR(255)
);

CREATE TABLE Supply (
    Sno VARCHAR(10),
    Pno VARCHAR(10),
    Quantity INT,
    PRIMARY KEY (Sno, Pno),
    FOREIGN KEY (Sno) REFERENCES Supplier(Sno),
    FOREIGN KEY (Pno) REFERENCES Parts(Pno)
);

```
#### 3. Data Insertion:
Three text files are saved to insert data into each table separately. Each data item is separated by a comma. Example datasets:

`supplier_data.txt:`
```
"S1", "Smith", 20, "London"
"S2", "Jones", 10, "Paris"
"S3", "Black", 30, "Paris"
"S4", "Clark", 20, "London"
"S5", "Adams", 30, "Athens"
```

`parts_data.txt:`
```
"P1", Nut, "Red", 12, "London"
"P2", Bolt, "Green", 17, "Paris"
"P3", Screw, "Blue", 17, "Rome"
"P4", Screw, "Red", 14, "London"
"P5", Cam, "Blue", 12, "Paris"
"P6", Cog, "Red", 19, "London"
```

`supply_data.txt:`
```
"S1", "P1", 300
"S1", "P2", 200
"S1", "P3", 400
"S1", "P4", 200
"S1", "P5", 100
"S1", "P6", 100
"S2", "P1", 300
"S2", "P2", 400
"S3", "P2", 200
"S4", "P2", 200
"S4", "P4", 300
"S4", "P5", 400
```

Data is uploaded from these text files to the tables using the LOAD command.
```
LOAD DATA LOCAL INFILE 'path to file/supplier_data.txt'
INTO TABLE Supplier
FIELDS TERMINATED BY ','
OPTIONALLY ENCLOSED BY '"'
LINES TERMINATED BY '\r\n';

LOAD DATA LOCAL INFILE 'path to file/parts_data.txt'
INTO TABLE Parts
FIELDS TERMINATED BY ','
OPTIONALLY ENCLOSED BY '"'
LINES TERMINATED BY '\r\n';

LOAD DATA LOCAL INFILE 'path to file/supply_data.txt'
INTO TABLE Supply
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\r\n';
```

#### Result :

Supplier:

| Sno | Sname | Status | City    |
|-----|-------|--------|---------|
| S1  | Smith | 20     | London  |
| S2  | Jones | 10     | Paris   |
| S3  | Black | 30     | Paris   |
| S4  | Clark | 20     | London  |
| S5  | Adams | 30     | Athens  |

Parts:

| Pno | Pname | Color | Weight | City    |
|-----|-------|-------|--------|---------|
| P1  | Nut   | Red   | 12     | London  |
| P2  | Bolt  | Green | 17     | Paris   |
| P3  | Screw | Blue  | 17     | Rome    |
| P4  | Screw | Red   | 14     | London  |
| P5  | Cam   | Blue  | 12     | Paris   |
| P6  | Cog   | Red   | 19     | London  |

Supply:

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



-- a) List Sno and Sname of suppliers whose status above 15.
```
SELECT Sno, Sname 
FROM Suppliers 
WHERE status > 15;
```
-- b) List the all cities in which parts are manufactured. (Remove duplicates from the answer).
```
SELECT DISTINCT city 
FROM Parts;
```

-- d) Deduct the status value by 2 for all suppliers.
```
UPDATE Suppliers 
SET status = status - 2;
```
-- e) List all suppliers by arranging them in descending order by status.
```
SELECT * 
FROM Suppliers 
ORDER BY status DESC;
```
-- f) Display the parts numbers and quantity of each part which are having quantity value greater than 300.
```
SELECT Pno, quantity 
FROM Parts 
WHERE quantity > 300;
```
-- g) List all the parts which have the color ‘Red’ or ‘Blue’.
```
SELECT * 
FROM Parts 
WHERE color IN ('Red', 'Blue');
```
-- h) List all the parts which have the color ‘Blue’ and city ‘Rome’.
```
SELECT * 
FROM Parts 
WHERE color = 'Blue' AND city = 'Rome';
```
-- i) List all the parts except Blue.
```
SELECT * 
FROM Parts 
WHERE color <> 'Blue';
```
-- j) List all names of Suppliers whose names having ‘I’ as the second letter.
```
SELECT Sname 
FROM Suppliers 
WHERE Sname LIKE '_I%';
```
-- k) Display name, city and weight of parts which are having weight between 12-17.
```
SELECT name, city, weight 
FROM Parts 
WHERE weight BETWEEN 12 AND 17;
```
