
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
