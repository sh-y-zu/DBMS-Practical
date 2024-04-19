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
| 1   | Nut   | Red   | 12     | London  |
| 2   | Bolt  | Green | 17     | Paris   |
| 3   | Screw | Blue  | 17     | Rome    |
| 4   | Screw | Red   | 14     | London  |
| 5   | Cam   | Blue  | 12     | Paris   |
| 6   | Cog   | Red   | 19     | London  |

Supply:

| Sno | Pno | Quantity |
|-----|-----|----------|
| S1  | 1   | 300      |
| S1  | 2   | 200      |
| S1  | 3   | 400      |
| S1  | 4   | 200      |
| S1  | 5   | 100      |
| S1  | 6   | 100      |
| S2  | 1   | 300      |
| S2  | 2   | 400      |
| S3  | 2   | 200      |
| S4  | 2   | 200      |
| S4  | 4   | 300      |
| S4  | 5   | 400      |

