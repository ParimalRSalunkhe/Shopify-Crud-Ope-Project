**github Project link : https://github.com/ParimalRSalunkhe/Shopify-Crud-Ope-Project.git**

======================================================================**How did you run the code ?** =======================================================================

Here’s how the code is run:

1. Using an Embedded Server (Tomcat):

Spring Boot comes with an embedded Tomcat server, so there is no need to configure a separate server manually.

Simply run the main method of the @SpringBootApplication class (e.g., Application.java) in Eclipse or your IDE.

The application will start and be accessible at http://localhost:8080 by default.


2. Steps to Run in Eclipse:

Open Eclipse and import the Spring Boot project.

Right-click on the main application class (annotated with @SpringBootApplication) and select Run As → Java Application.

The Spring Boot application will start, and logs will confirm the embedded Tomcat server is running.

Use a REST client like Postman or a browser to test the APIs.


3. Access APIs:

After running the application, the APIs will be accessible at:

http://localhost:8080/api/categories

http://localhost:8080/api/products


4. Database Connection:

Ensure your MySQL (or any configured RDBMS) is running, and the database credentials in application.properties are correct.

The tables (category and product) will be auto-created by Hibernate based on the entity configurations.


=============================================================================**How did you run the machine test ?** ===================================================================

I run the machine test by using the Eclipse IDE

Steps to Run the Machine Test:

1. Import the Project:

Imported the Spring Boot project as a Maven Project into Eclipse.


2. Set Up the Database:

Ensured the database (e.g., MySQL) was running.

Configured database credentials in the application.properties file.


3. Run the Application:

Opened the main class annotated with @SpringBootApplication (e.g., Application.java).

Right-clicked on the main class → Run As → Java Application.

This started the embedded Tomcat server, and the application was available at http://localhost:8080.


4. Test the APIs:

Used Postman to test each API:

Performed CRUD operations for both Category and Product entities.

Verified the expected behavior of APIs like GET, POST, PUT, and DELETE.


5. Verified Database Changes:

Confirmed data was being stored, updated, and deleted in the MySQL database by querying the respective tables.


=======================================================================**DB Design**=====================================================================

1. Category Table

Stores information about categories.
CREATE TABLE category (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


2. Product Table

Stores information about products and their association with categories.
CREATE TABLE product (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL,
    category_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES category(id) ON DELETE CASCADE
);

Application Properties

Add DB configuration to application.properties:
spring.datasource.url=jdbc:mysql://localhost:3306/your_database_name
spring.datasource.username=your_username
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

Entity Relationship

One-to-Many Relationship: A Category can have multiple Products.
Foreign Key: The category_id in the product table links to the id in the category table.


ER Diagram

Category Table (Parent)

id (Primary Key)

Product Table (Child)

id (Primary Key)
category_id (Foreign Key → Category.id)
