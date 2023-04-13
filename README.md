# Task-SQL_Scripts
Task-SQL_Scripts


Create database StudentRecords

go

use StudentRecords

go

create schema MainSchema

go

CREATE TABLE MainSchema.Users (
  UserID INT IDENTITY(1,1) PRIMARY KEY,
  UserName VARCHAR(50) NOT NULL,
  Password VARCHAR(50) NOT NULL
);

CREATE TABLE MainSchema.Countries (
  CountryID INT IDENTITY(1,1) PRIMARY KEY,
  CountryName VARCHAR(50) NOT NULL
);

CREATE TABLE MainSchema.Cities (
  CityID INT IDENTITY(1,1) PRIMARY KEY,
  CityName VARCHAR(50) NOT NULL,
  CountryID INT NOT NULL,
  CONSTRAINT FK_Cities_Countries FOREIGN KEY (CountryID) REFERENCES MainSchema.Countries(CountryID)
);

CREATE TABLE MainSchema.Courses (
  CourseID INT IDENTITY(1,1) PRIMARY KEY,
  CourseName VARCHAR(50) NOT NULL
);

create Table MainSchema.Students
(
	StudentID int identity (1,1) primary key,
	"FirstName" varchar (50) NOT NULL,
	"LastName" varchar (50) NOT NULL,
	"Date of Birth" date NOT NULL,
	Gender varchar (50) NOT NULL,
	"Address Line 1" varchar (100) NOT NULL,
	Email varchar (50) NOT NULL,
	"Phone Number" varchar (50) NOT NULL,
	SSN varchar(100) NULL,
	"Address Line 2" varchar(100) NULL,
	CityID int NOT NULL,
	CountryID int NOT NULL,
	CourseID int NOT NULL,
	"Course Start Date" varchar(100) NULL,
	"News Letter Consent" varchar(100) NULL,
    CONSTRAINT FK_Students_Cities FOREIGN KEY (CityID) REFERENCES MainSchema.Cities(CityID),
    CONSTRAINT FK_Students_Countries FOREIGN KEY (CountryID) REFERENCES MainSchema.Countries(CountryID),
    CONSTRAINT FK_Students_Courses FOREIGN KEY (CourseID) REFERENCES MainSchema.Courses(CourseID)
);
