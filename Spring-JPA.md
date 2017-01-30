###Introduction
The Java Persistence API is a Java specification for accessing, persisting, & managing data between Java Objects/Classes and relational database.Defined as a part of EJB 3.0. JPA is considered the standard industry approach for ORM like Hibernate, Spring Data etc.

* JPA is specification .i.e it tells any ORM what interfaces to expose to application developers
* JPA is just a specification & not a product, it cannot perform persistence or anything else by itself.
* JPA is just a set of interfaces, and requires implementation. There are open-souce & commercial JPA implementation to choose from.
* JPA needs database to persist data.

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>


##Code
###CrudRepository
