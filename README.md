# Pets Database
Develop SQL statements required to manipulate a database of pets<br>

[data types](https://www.w3schools.com/sql/sql_datatypes.asp),
[hsqldb](http://hsqldb.org/),
[sql](https://www.w3schools.com/sql/),
[uuid](https://www.uuidgenerator.net/)

## Pre-requirements
* Ensure the Eclipse IDE has Maven by looking for M2E from Help About ([details](https://www.vogella.com/tutorials/EclipseMaven/article.html))
* Install `DBViewer Plugin 1.2.2.v20101009` by ZIGEN from the Eclipse IDE marketplace
* Import into Eclipse as Git with smart import (accepting all defaults in wizard)
* Let the IDE finish building dependencies before proceeding (see bottom right of Eclipse)

## Steps
* Run the PetsDB app to start the database
* Develop Pets-based SQL statements
* Switch to DBViewer perspective to test
* Stop the PetsDB app to shutdown database
* Ensure SQL documented within this README
* Push update README back to forked GitHub

## Bonus
* Create another related table with SQL
CREATE TABLE FoodStore (Id CHAR(36), Name VARCHAR(100),Town VARCHAR(100), OwnerId CHAR(36), PRIMARY KEY(Id), FOREIGN KEY (OwnerId) REFERENCES Owner(Id))
INSERT INTO FoodStore (Id, Name, Town, OwnerId) VALUES ('6b7999e2-dc0f-4a58-89e7-9a84fb7f286e', 'Pets', 'Coventry','bb2e7432-9512-4ca5-a6ae-75204daf9966')

## Database Schema

**Animal table**
 - Hunger INT
 - Id CHAR(36)
 - Name VARCHAR(100)
 - OwnerId CHAR(36)
 - Species CHAR(1)

**Owner table**
 - Id CHAR(36)
 - Name VARCHAR(100)
 - Town VARCHAR(100)
 
**To create the Owner table**<br>
CREATE TABLE Owner (Id CHAR(36), Name VARCHAR(100),Town VARCHAR(100), PRIMARY KEY(Id))

**To create the Animal table**<br>
CREATE TABLE Animals (Id CHAR(36), Name VARCHAR(36), OwnerId CHAR(36), Hunger INT, Species CHAR(1), PRIMARY KEY (Id), FOREIGN KEY (OwnerId) REFERENCES Owner(Id))

**To insert a new Owner row**<br>
INSERT INTO Owner (Id, Name, Town) VALUES ('bb2e7432-9512-4ca5-a6ae-75204daf9966', 'Bob', 'Coventry')

**To insert a new Cat row**<br>
INSERT INTO Animals (Id, Name, OwnerId, Hunger, Species) VALUES ('8282ea26-e683-4b2b-823b-9a11708940e7', 'Rob', 'bb2e7432-9512-4ca5-a6ae-75204daf9966', 9, 'C')

**To insert a new Dog row**<br>
INSERT INTO Animals (Id, Name, OwnerId, Hunger, Species) VALUES ('9961e9e7-414c-4c59-85a1-d25ce4a14ef3', 'Bob', 'bb2e7432-9512-4ca5-a6ae-75204daf9966', 10, 'D')

**To query an animal**<br>
SELECT Animals.Name FROM Animals animals WHERE animals.Name = 'Bob'

**To query all pets for an owner**<br>
SELECT Animals.Name FROM Owner owner, Animals animals WHERE owner.Name = 'Bob' AND animals.OwnerId = Owner.Id

