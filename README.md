# Squizer

## Build
This project is built with Maven. It uses Spring and Spring MVC as architecture. The database is mounted by hibernate, whose generation options are in application.properties.

This project was build on Ubuntu 18.04, during a professional training session.

## Install
First run (detailed process with command line) :

Install default java jdk sudo apt install defaul-jdk Install mysql and create the database 'Quizz'. sudo apt install mysql-server `sudo mysql -p` (enter your passphrase) 
> CREATE DATABASE Quizz;
> Create user 'Admin' identified by 'Password';

You can also choose a username and a personalized password, but if so, you will also have to enter it in the `application.properties` file.

> CREATE USER 'Admin'@'localhost' IDENTIFIED BY 'Password'; GRANT ALL PRIVILEGES ON Quizz.* TO 'Admin'@'localhost'; Rename --Data.sql to data.sql to use default database with default Admin. If so, set in application.properties spring.jpa.hibernate.ddl-auto=create

Place yourself in src/main/java/a84/squizer folder ./mvnw spring-boot:run It is possible that the execution rights are not granted to the ./ folder, to solve this problem you can enter the next line : chmod +x ./mvnw You can rename data.sql to whatever then, so on reboot it will not erase your data, and in application.properties : spring.jpa.hibernate.ddl-auto=none

You can also change the port, in src/main/java/a84/squizer/Squizer.java, search for line 11 : System.setProperty("server.port", "xxxx"); and change it to : System.setProperty("server.port", "80"); or something else.

You can authentify by default : Name : Administrateur; Passphrase : Fv4xLRzMftz8SKRL; You can change these credentials in data.sql located in the ressources folder, entering an hashed password and its seed.

Improvements are to be made soon : Adding pieces of javascript Polish on the members administration page Creation of the administrator account at the first connection. Security against DDOS attacks to be perfected. Complete the clues function, which for now gives the clue by hovering the mouse over a “?”. A check should be done on the server side to check if the quiz has already been taken, and if so, indicate the clue. Transform receiving text for text responses, making it case-insensitive Make invisible the fields not necessary when entering responses. For example, a single true answer cannot be worth 0, negative “button” responses cannot be worth points. Code a random quiz function (randomly asking 5, 10, 20 questions already existing in the database, creating a new random quiz for this) Some response types, when entered when creating a quiz, cause the site to crash if the value selected is 0. The creator of a quiz should be the only one (with the admin) by default able to modify it, and elect members of the site so that they have editing rights on it, if he wishes to share these rights. Delete the data.sql file, which is used to inject the administrator for the first user. Has to be injected from the firstrun.java file
