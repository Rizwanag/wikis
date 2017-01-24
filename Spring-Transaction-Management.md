###Transaction Management Objectives
* A db tx is a sequence of actions that is treated as a single unit of work.
* These actions should either complete entirely or take no effect at all.
* Tx Mgmt is an important aspect to ensure data integrity & consistency. 
* Key Properties of Transactions
  - Atomicity   : Tx should be treated as a single unit of operations 
  - Consistency : Make sure stored data is all right, unique primary keys etc.
  - Isolation   : Many tx processes same data at same time. Isolating the tx, so that data is not corrupted.
  - Durability  : The results of tx should be persisted & not erased due to crash.
* Spring framework provides an abstract layer on top of different tx mgmt API's.
* It intends to provide transaction capabilities to POJOs. 
 

# Introduction
Spring Framework provides an abstraction for transaction management. It's functionalities are
 * Various transaction API's supported by Spring - Java Transaction APIs, JDBC, Hibernate, Java Data Objects, JPA etc. Tx  programming is same across all.
 * Supports Declarative Tx. Mgmt.It very less pollutes business code.   
 * Simpler API's compared to JTA
 * Awesome integration with Spring's data access abstractions.

#  Advantages of Spring Framework's Tx. Model
Two common choices of Tx. Mgmt. - Global Tx. & Local Tx.
 *  Global Transaction - Enables to work with multiple transactional resources like db or message queues. Done using JTA, which was very cumbersome.
 *  Local Transaction - Resource specific like JDBC. But, this cannot access multiple transactional resources. Most of the transaction will be local.
 *  Spring provides consistent programming model for both the above transaction.

###Local vs Global Transactions
* Local transactions are specific to single transaction resource.
* Local Transaction is useful in centralized computing environment, where application components & resources are located in single site & transaction manager involves a local data manager ( everything is in single machine ).

* Global transactions can span across multiple transaction resources like distributed system.
* A global transaction is executed across distributed multiple systems.
* It's much more complex.

###Programmatic & declarative transaction
* Programmatic - Manage Tx using flexible programs
* Declarative - Separates Tx from business code, no coding involved. Just declaration.
* Declative is preferred as it can be controller with AOP.  

# Code Understanding of Spring Transaction  
 *  Transaction Strategy defined in `org.springframework.transaction.PlatformTransactionmanager` interface. This is primary service provider interface (SPI)
    Functions in this - getTransaction(TransactionDefination), commit, rollback. 
 *  Any bean which wants to manage tx. can implement this interface. Spring Framework IoC container contains all beans.
 *  getTransaction - returns TransactionStatus object. Can be a new Tx or existing one. 
 *  TransactionDefination 
           - Isolation : How isolated this tx. is from other tx.
           - Propagation : Usually, all code executed in tx. scope will return in tx. Suspend existing tx and new tx. can be created.
           - Timeout: How long the tx. can be carried out
           - Read-only status : Tx. code on reads data & doesn't modify anything.  

# Synchronizing resources with transactions
 * To synchronize transaction, you need transactional managers - for JDBC DataSource, DataSourceTransactionalManager. For Hibernate Sessionfactory, it would be HibernateTransactionManager  


# Declarative transaction management
 * Least impact in application code, thus non-invasive.  
 
##Example Explanation
* Database details - name more than 5 characters not allowed
* AppRunner - CommandLineRunner    

###Dependencies

    <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-jdbc</artifactId>
    </dependency>

    <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <scope>runtime</scope>
    </dependency>

###Explanation of sample application
* Create a database with a constraint - ( fname not more than 5 chars )
* Implement run function in CommandLineRunner & annotate with @Component.

