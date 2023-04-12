# RestAPISample

Documentation for building and testing Rest API for a Cloudvendor Information Service using Java 17, SpringBoot, MySQL, Postman.

Software requirements:
Java installed in local.
IntelliJ (IDE),
MySQL,
Postman.

 CloudVendor Information service

Here we are building three layers.

Controller Layer
Business/Service Layer
Database/Repository Layer

 

Here are the Properties of Cloud Vendor API

Cloud Vendor API Properties
Vendor ID,
Vendor Name,
Vendor Address,
Vendor Phone Num.

To create the RestAPI project, we use https://start.spring.io/ to download the dependencies that are required for creating and connecting the REST API to MySQL server are

Spring Web, 	Spring data JPA, and 	MySQL Driver.

For this project we are creating in Maven Project, Java language, SpringBoot version as 2.7.10,  
Open this zip file in any IDE to add or changes that we needed.

We can see the dependencies that are used in the project in pom.xml file if you need any dependencies we can add manually in this file. 
NOTE: If you add any dependency manually then you should perform Maven rebuild. Then it will add to your file.


RestApiDemo -> src -> main -> java -> com.SampleApi.RestAPIDemo -> model (Create package)

In the model folder create a new java class with name CloudVendor. As we created some entities to store the data we created (vendorID, vendorName, vendorAddress, vendorPhoneNumber) Also created constructor for these entities along with one empty constructor, create getter and setters for all the entitles which we are going to use.
Use @Entity to denote this as Entity class and add @Table to give a specific table name to store these entities.
Which field you decided to add as Id mention that field as @Id
NOTE: Make sure that @Entity, @Id and @Table are coming from javax.persistence


RestApiDemo -> src -> main -> java -> com.SampleApi.RestAPIDemo -> Contoller (Create package)

After the model, create cloudVendorController class as we perform CURD operations here. We use 
@Restcontroller to identify it is a controller class and we use 
@Requestcontroller to map and identify the endpoint for this API.
If needed we can also add more business logic in this class.

All the configuration related to database are done in application.yaml file. For that, create a life in resource folder. Before that, make sure to connect with the database localhost and create a schema in MySQL. I created schema as Cloud_Vendor.

Create CouldVendorService instance here to access the service layer. Also generate constructor for that. 

(we need to write the URL: and it should be start with JDBC. Followed with the IDE which we are using for query(MySQL) Localhost:3306 is the default port for any mysql to run. Cloud_vendor is the schema name where we are creating tables and store the data.
If we are using any SSL certificate to authenticate we set SSL=true or else set to false.
Username and password are for mysql to connect with.)


RestApiDemo -> src -> main -> java -> com.SampleApi.RestAPIDemo -> Repository (Create package)

Now, create an Interface with the name as CloudVendorRepository. Extend this class with JpaRepository as it gets from org.springframework.data.jpa.repository so that we can use the build-in methods from this class. 
If you need, you can also add custom methods in this class.


RestApiDemo -> src -> main -> java -> com.SampleApi.RestAPIDemo -> Service (Create package)

Now, create an interface with name CloudVendorService. Here we will mention what are the actions that we are going to perform in the APIs we will mention in this interface.

After this, we need to implement it. 


RestApiDemo -> src -> main -> java -> com.SampleApi.RestAPIDemo -> impl (Create package)

Now create CloudVendorServiceImpl class in this package. Here we implement cloudVendorService, and then implement all the methods that are mentioned in the interface.
Here we initiated cloudVendorRepository and implement it. We have to denore @Service notation to recognize it as service. 
Here we need to save, update, find and delete the data in database using save(), findbyId(), and deletebyID() method and enter the entity value.
Also we can implement more business logic if we need to perform more operations inside it. 


After finishing and implementing all the requirements in the code, run the application. Once the application is started, you can see the table is created in the mysql database. We can add the data and perform CRUD operations in the postman using endpoint that we created earlier.	
![image](https://user-images.githubusercontent.com/130108971/231594953-45a6e391-f8e7-40b9-ad97-2a4af24da554.png)
