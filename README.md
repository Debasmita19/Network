Got it. Here's the updated schema for all three tables with the foreign key constraints added:

```sql
CREATE TABLE Users (
    Employee_Id INTEGER PRIMARY KEY,
    First_Name VARCHAR(15),
    Last_Name VARCHAR(10),
    Phone_Number VARCHAR(10),
    Email_Address VARCHAR(50),
    Role VARCHAR(15),
    Max_Passengers_Allowed INTEGER,
    Fare_Per_KM INTEGER,
    Assigned_On DATE,
    CurrentGradeId INTEGER,
    FOREIGN KEY (CurrentGradeId) REFERENCES Grades(Id)
);

CREATE TABLE Grades (
    Grade_Id INTEGER PRIMARY KEY,
    Name VARCHAR(25),
    Max_Passengers_Allowed INTEGER,
    Fare_Per_KM INTEGER,
    Assigned_On DATE,
    Employee_Id INTEGER,
    FOREIGN KEY (Employee_Id) REFERENCES Users(Employee_Id)
);

CREATE TABLE GradesHistory (
    Id INTEGER PRIMARY KEY,
    Assigned_On DATE,
    Employee_Id INTEGER,
    Grade_Id INTEGER,
    Max_Passengers_Allowed INTEGER,
    Fare_Per_KM INTEGER,
    FOREIGN KEY (Employee_Id) REFERENCES Users(Employee_Id),
    FOREIGN KEY (Grade_Id) REFERENCES Grades(Grade_Id)
);
```

These schemas create the tables with the specified columns and add the foreign key constraints as requested. Let me know if you need any further adjustments!





Debasmita
Sure, here's an example of a data SQL script for your schema:

```sql
-- Insert data into VehicleTypes table
INSERT INTO VehicleTypes (Id, Max_Passengers_Allowed, Fare_Per_KM)
VALUES
    (1, 5, 10),
    (2, 4, 12),
    (3, 7, 8);

-- Insert data into Vehicles table
INSERT INTO Vehicles (Registration_No, BelongsTo_User_Id, Vehicle_Type_Id, Inspection_Status, Inspected_By_User_Id, Inspected_On)
VALUES
    ('ABC123', 1, 1, 'In', 88, '2024-02-27'),
    ('XYZ456', 2, 2, 'Ir', 89, '2024-02-28'),
    ('LMN789', 3, 1, 'PL', 90, '2024-03-01');

-- Insert data into VehicleDetails table
INSERT INTO VehicleDetails (Registration_No, RTO_Name, Registration_Date, Registration_Expires_On, RC_Doc_URL, Insurance_Company_Name, Insurance_No, Insuranced_On, Insurance_Expires_On, Insurance_Certificate_DOC_URL, PUC_Certificate_No, PUC_Issued_On, PUC_Valid_Until, PUC_DOC_URL, Accessibility_Investigate, Search)
VALUES
    ('ABC123', 'RTO1', '2023-01-01', '2024-01-01', 'url1', 'Company1', 12345, '2023-01-01', '2024-01-01', 'url1', 54321, '2023-01-01', '2024-01-01', 'url1', 'Yes', 'No'),
    ('XYZ456', 'RTO2', '2023-02-01', '2024-02-01', 'url2', 'Company2', 67890, '2023-02-01', '2024-02-01', 'url2', 09876, '2023-02-01', '2024-02-01', 'url2', 'No', 'Yes'),
    ('LMN789', 'RTO3', '2023-03-01', '2024-03-01', 'url3', 'Company3', 13579, '2023-03-01', '2024-03-01', 'url3', 24680, '2023-03-01', '2024-03-01', 'url3', 'Yes', 'No');
```

This script inserts sample data into each of your tables. Adjust the values as needed for your actual data. Let me know if you need further assistance!


Certainly! Here's the updated schema for all three tables without the `IF NOT EXISTS` clause:

```sql
CREATE TABLE VehicleTypes (
    Id INTEGER PRIMARY KEY,
    Max_Passengers_Allowed INTEGER NOT NULL,
    Fare_Per_KM INTEGER NOT NULL
);

CREATE TABLE Vehicles (
    Registration_No VARCHAR(10) PRIMARY KEY,
    BelongsTo_User_Id INTEGER NOT NULL,
    Vehicle_Type_Id INTEGER NOT NULL,
    Inspection_Status VARCHAR(10) NOT NULL,
    Inspected_By_User_Id INTEGER NOT NULL,
    Inspected_On DATE NOT NULL,
    FOREIGN KEY (Vehicle_Type_Id) REFERENCES VehicleTypes(Id)
);

CREATE TABLE VehicleDetails (
    Registration_No VARCHAR(10) PRIMARY KEY,
    RTO_Name VARCHAR(10) NOT NULL,
    Registration_Date DATE NOT NULL,
    Registration_Expires_On DATE NOT NULL,
    RC_Doc_URL VARCHAR(100) NOT NULL,
    Insurance_Company_Name VARCHAR(50) NOT NULL,
    Insurance_No INTEGER NOT NULL,
    Insuranced_On DATE NOT NULL,
    Insurance_Expires_On DATE NOT NULL,
    Insurance_Certificate_DOC_URL VARCHAR(100) NOT NULL,
    PUC_Certificate_No INTEGER NOT NULL,
    PUC_Issued_On DATE NOT NULL,
    PUC_Valid_Until DATE NOT NULL,
    PUC_DOC_URL VARCHAR(100) NOT NULL,
    Accessibility_Investigate VARCHAR(10) NOT NULL,
    Search VARCHAR(10) NOT NULL,
    FOREIGN KEY (Registration_No) REFERENCES Vehicles(Registration_No)
);
```

This creates all three tables without checking if they already exist. Let me know if you need further assistance!


Here's the schema for all three tables written in a single query following the specified pattern:

```sql
CREATE TABLE IF NOT EXISTS VehicleTypes (
    Id INTEGER PRIMARY KEY,
    Max_Passengers_Allowed INTEGER,
    Fare_Per_KM INTEGER
);

CREATE TABLE IF NOT EXISTS Vehicles (
    Registration_No VARCHAR(10),
    BelongsTo_User_Id INTEGER,
    Vehicle_Type_Id INTEGER,
    Inspection_Status VARCHAR(10),
    Inspected_By_User_Id INTEGER,
    Inspected_On DATE,
    PRIMARY KEY (Registration_No),
    FOREIGN KEY (Vehicle_Type_Id) REFERENCES VehicleTypes(Id)
);

CREATE TABLE IF NOT EXISTS VehicleDetails (
    Registration_No VARCHAR(10),
    RTO_Name VARCHAR(10),
    Registration_Date DATE,
    Registration_Expires_On DATE,
    RC_Doc_URL VARCHAR(100),
    Insurance_Company_Name VARCHAR(50),
    Insurance_No INTEGER,
    Insuranced_On DATE,
    Insurance_Expires_On DATE,
    Insurance_Certificate_DOC_URL VARCHAR(100),
    PUC_Certificate_No INTEGER,
    PUC_Issued_On DATE,
    PUC_Valid_Until DATE,
    PUC_DOC_URL VARCHAR(100),
    Accessibility_Investigate VARCHAR(10),
    Search VARCHAR(10),
    PRIMARY KEY (Registration_No),
    FOREIGN KEY (Registration_No) REFERENCES Vehicles(Registration_No)
);
```

This creates all three tables with the specified columns and constraints in a single query. Let me know if you need any further adjustments!
