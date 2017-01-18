Steps to Create SpringMVC Project
* Create the following package -
  1. Controller - Provides controller functionalities
  2. DAO  - Talks to hibernate
  3. Model  - Contains all models. Models are class definitions, where their tables will be created in database. 
  4. Service - But, we need to provide services for the models. Possible services can be CURD operations. 

###DAO
* DAO is dependent on SessionFactory
* This is for database abstraction of an object. To map something to database, create a DAO of it. 
* Whenever, we save something in DAO. It gets saved into database.
* DAO abstracts persisting mechanism. 
* DAO is the owner of sessionfactory.

###Service Classes
* Service class dependent on DAO class object.
* This contains reference to DAO so that, it can send person objects to database.
* Service class of a model provides application functionality that a model intends to provide.

###Controller Classes
* Controller dependent on Service Class object
* This is the entry point of user request.
* Controller functions gets information from models using service classes.
 
##Configuration
###web.xml
* DispatcherServlet
* Configurational file for dispatcher-servlet

###Config file of Dispatcher Servlet
* SpringMVC annotation
* Static Resources
* InternalViewResolver
* Package information of controller classes
* DataSource config -
   - DataSource is an object/bean which contains all the information of database connection.
* SessionFactory bean requirement
   - Authentication - datasource
   - Table information - Mapped class name
   - What to access - Hibernate in this case

###Bean Creations
* Create a datasource
* Create a hibernateSessionFactory which is dependent on datasource & provide all hibernate configuration
* Create a DAO bean will have dependency on session-factory
* Create a service bean, this will have dependency on DAO
* Create a transactionmanager bean, this will have dependency on session-factory.

###Transactional
* All the actions in a function that is annotated with @Transactional, will be complete or partially completed things will be rolled back.

###Flow
* Request reaches controller
* Controller talks to Service classes
* Services invokes DAO layer
* DAO talks to hibernate
* Hibernate talks to database.