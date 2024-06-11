# NYC-Payroll-DatawareHouse
This repository contains the schema and stored procedures for the Enterprise Data Warehouse (EDW) designed to manage and analyze NYC payroll data. It includes SQL scripts for creating necessary tables and a stored
Enterprise Data Warehouse (EDW) for NYC Payroll Data
This repository contains the schema and stored procedures for the Enterprise Data Warehouse (EDW), which is designed to manage and analyze NYC payroll data. It includes SQL scripts for creating necessary tables and a stored procedure to load data from staging tables into the EDW. The data warehouse integrates various payroll datasets, ensuring data integrity and facilitating comprehensive reporting and analysis.

Table of Contents
Overview
Schema Details
Stored Procedures
Getting Started
Usage
Contributing
License
Overview
The Enterprise Data Warehouse (EDW) is built to support NYC payroll data, providing a robust and scalable architecture for data storage, integration, and analysis. The EDW schema and stored procedures help maintain data consistency and accuracy across various payroll datasets.

Schema Details
Tables
CREATE TABLE EDW.AgencyMaster (
    AgencyID int PRIMARY KEY,
    AgencyName text
);

CREATE TABLE EDW.EmpMaster (
    EmployeeID INT PRIMARY KEY,
    LastName VARCHAR(100),
    FirstName VARCHAR(100)
);

CREATE TABLE EDW.TitleMaster (
    TitleCode INT PRIMARY KEY,
    TitleDescription VARCHAR(100) 
);

CREATE TABLE EDW.TitleMaster (
    TitleCode INTEGER PRIMARY KEY,
    TitleDescription TEXT
);


CREATE TABLE EDW.nycpayroll_2020(
    FiscalYear TEXT,
    PayrollNumber INTEGER,
    AgencyID INTEGER,
    AgencyName TEXT,
    EmployeeID INTEGER,
    LastName TEXT,
    FirstName TEXT,
    AgencyStartDate VARCHAR(15),
    WorkLocationBorough TEXT,
    TitleCode INTEGER,
    TitleDescription TEXT,
    LeaveStatusasofJune30 TEXT,
    BaseSalary NUMERIC,
    PayBasis TEXT,
    RegularHours NUMERIC,
    RegularGrossPaid NUMERIC,
    OTHours NUMERIC,
    TotalOTPaid NUMERIC,
    TotalOtherPay NUMERIC,
    FOREIGN KEY (AgencyID) REFERENCES EDW.AgencyMaster(AgencyID),
	FOREIGN KEY (TitleCode) REFERENCES EDW.TitleMaster(TitleCode)
    );

CREATE TABLE EDW.nycpayroll_2021 (
    PayrollNumber INTEGER PRIMARY KEY,
    FiscalYear TEXT,
    AgencyID INTEGER,
    AgencyName TEXT,
    EmployeeID INTEGER,
    LastName TEXT,
    FirstName TEXT,
    AgencyStartDate VARCHAR(15),
    WorkLocationBorough TEXT,
    TitleCode INTEGER,  
    TitleDescription TEXT,
    LeaveStatusasofJune30 TEXT,
    BaseSalary NUMERIC,
    PayBasis TEXT,
    RegularHours NUMERIC,
    RegularGrossPaid NUMERIC,
    OTHours NUMERIC,
    TotalOTPaid NUMERIC,
    TotalOtherPay NUMERIC,
    FOREIGN KEY (AgencyID) REFERENCES EDW.AgencyMaster(AgencyID),
    FOREIGN KEY (TitleCode) REFERENCES EDW.TitleMaster(TitleCode)  
);
