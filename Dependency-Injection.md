###IoC
* IoC is a mechanism where objects define their dependencies, that is, the objects they work together. The container/spring injects those dependencies after creation of beans. This is inverse of regular process & hence called Inversion of Control. This is same as dependency injection. 

1. If there are two completely unrelated classes, changes in one will have no impact on other. 
2. Classes cannot work without relationships with other classes.
3. So, there needs to be a mechanism to connecting classes (dependency).
4. Dependency between classes was solved by making dependency class member of dependent class.
5. By making one class member of other class, it becomes responsibility of the dependent class to take care of everything.

###Types of Coupling
* Not coupled - Changes in once classhas no relevence in other class.
* Tightly coupled - Changes in one class costs other class to change as well.
* Loosely Coupled - Two classes are related but changes in one don't have impact on other. 

##Terms
* Dependent Class - e.g. CarShowroom, The class which is dependent on dependency class
* Dependency Class - e.g. Car, The class which is being dependent on.

### Definations
* Beans - Object of a POJO classes.
* Container - Holder of all beans

## Annotations
1. @Configuration - This tells spring framework about the class that is capable of providing functions to create beans 
2. @Bean - This tells spring framework about the functions capable of creating beans 
3. @Scope - This tells spring the object type - singleton or prototype. 
4. @Qualifier - Tells which bean to connect
5. @Autowired - Connect dependency to dependent

### What Spring provides ?
* It takes the responsibility of object creation & entire life-cycle.
* It creates both dependent class objects & dependency class objects.
* It wires/develops the responsibility of correcting objects/beans of different classes.
 
* ApplicationContext - Using this interface, application can request spring framework to create objects. 
* AnnotationConfigApplicationContext - Implementation class
* Beans by default are singleton.@Scope can be used to make them prototype

###Using Spring to create objects
* Create a Maven Project, add dependecies

`    <dependency>`
    `<groupId>org.springframework</groupId>`
    `<artifactId>spring-context</artifactId>`
    `<version>4.3.1.RELEASE</version>`
    `</dependency>`

###ApplicationContext
* This is an interface provided by Spring Framework.
* The main purpose of application context is to provide configuration to the spring application.
* There are many implementation of this interface
  - AbstractApplicationContext
  - FileSystemXmlApplicationContext
  - AnnotationConfigApplicationContex
  - XmlWebApplicationContext

* For e.g. AnnotationConfigApplicationContex takes class name as an input. This class provides mechanism to build beans. 
  - When we run the application, spring take's the argument class of AnnotationConfigApplicationContex.
  - @Configuration tells spring framework that this class will contain functions that is capable of creating beans.
  - @Bean tells spring that the function following it should be executed to create beans in the startup.
  - The beans will be floating in the Spring Container.

###Type of Beans
* Unnamed Beans - beans created without name @Bean. It should be only one, or else creates confusion to spring framework.This is also known as wiring by type.
* Named Beans - beans created with name  @Bean(name="bata2"). This is used in wiring by name.
 
###Scope
* Singleton/Default - On every getbean, it returns reference of the same object. The only bean gets created during bootup. 
* Propotype - On every getbean, it returns reference of new object. The bean is created during getContext.
* Request - The bean with @Request scope is alive in the lifetime request message only.
* Session - The bean with @Session scope is alive in the lifetime request message only.
  
###Types of auto-wiring
* When spring boots up ( when you start the application ), it identifies the dependencies by finding @Autowired.
* It looks for the dependent beans in Spring Container. And, it connects the beans.
* During bootup reading bean configuration file, spring would have created beans.
* By Type - Spring tries to find dependency bean of dependent class using only type information. If no confusion is raised ( not a case of multiple beans of same type )
* By Name - Using @Qualifier, application code can tell the specific bean the dependent class has dependency. And, it connects to it.
* A Prototype bean can be dependent on singleton bean. And, vice-versa  