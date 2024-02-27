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
