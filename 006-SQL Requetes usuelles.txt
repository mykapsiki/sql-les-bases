##############################
Requêtes SQL SELECT simples
##############################

#A) SELECT pour récupérer une colonne d’une table
SELECT lastName FROM employees;
#B) SELECT pour récupérer plusieurs colonnes d’une table
SELECT lastname, firstname, jobtitle FROM employees;
#C) SELECT pour récupérer toutes les colonnes d’une table
SELECT * FROM employees; (Pas recommandé)

#D) clause ORDER BY pour trier les valeurs d’une colonne
SELECT contactLastname, contactFirstname FROM customers ORDER BY contactLastname; (ASC par défaut)

#E) clause WHERE avec l’opérateur =
SELECT lastname, firstname, jobtitle FROM employees WHERE jobtitle = 'Sales Rep';

#F) clause WHERE avec l’opérateur and 
SELECT lastname, firstname, jobtitle, officeCode FROM employees WHERE jobtitle = 'Sales Rep' AND officeCode =1;

##############################
#Requêtes SQL SELECT avec JOIN
##############################

SELECT 
    productCode, 
    productName, 
    textDescription
FROM
    products t1
INNER JOIN productlines t2 
    ON t1.productLine = t2.productLine;

##############################
#    Requêtes SQL INSERT INTO
##############################

#A) INSERT simple dans une table
INSERT INTO tasks(title,priority)
VALUES('Learn MySQL INSERT Statement',1);


#B) INSERT avec des dates - utiliser le format 'YYYY-MM-DD'
INSERT INTO tasks(title, start_date, due_date)
VALUES('Insert date into table','2018-01-09','2018-09-15'); 

#C) INSERT de valeurs multiples
INSERT INTO tasks(title, priority)
VALUES
	('My first task', 1),
	('It is the second task',2),
	('This is the third task of the week',3); 

##############################
#Requêtes SQL UPDATE
##############################

#A) UPDATE pour modifier la valeur d’une seule colonne
UPDATE employees 
SET 
    email = 'mary.patterson@classicmodelcars.com'
WHERE
    employeeNumber = 1056;

#B) UPDATE pour modifier les valeurs de plusieurs colonnes
UPDATE employees 
SET 
    lastname = 'Hill',
    email = 'mary.hill@classicmodelcars.com'
WHERE
    employeeNumber = 1056; 

##############################
#Requêtes SQL DELETE
##############################

#A) DELETE all rows
DELETE FROM employees;

#B) DELETE one or few rows
DELETE FROM employees 
WHERE officeCode = 4;

#C) DELETE and LIMIT
DELETE FROM customers
WHERE country = 'France'
ORDER BY creditLimit
LIMIT 5; 

##############################
#Requêtes SQL CREATE TABLE
##############################

CREATE TABLE projects(
	project_id INT AUTO_INCREMENT, 
	name VARCHAR(100) NOT NULL,
	start_date DATE,
	end_date DATE,
	PRIMARY KEY(project_id)
);

INSERT INTO 
	projects(name, start_date, end_date)
VALUES
	('AI for Marketing','2019-08-01','2019-12-31'),
	('ML for Sales','2019-05-15','2019-11-20');

##############################
#Requêtes SQL DROP TABLE
##############################

CREATE TABLE insurances (
    id INT AUTO_INCREMENT,
    title VARCHAR(100) NOT NULL,
    effectiveDate DATE NOT NULL,
    duration INT NOT NULL,
    amount DEC(10 , 2 ) NOT NULL,
    PRIMARY KEY(id)
);

DROP TABLE insurances;


CREATE TABLE CarAccessories (
    id INT AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    price DEC(10 , 2 ) NOT NULL,
    PRIMARY KEY(id)
);

CREATE TABLE CarGadgets (
    id INT AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    price DEC(10 , 2 ) NOT NULL,
    PRIMARY KEY(id)
);

DROP TABLE CarAccessories, CarGadgets;

