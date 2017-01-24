http://www.baeldung.com/spring-cache-tutorial

ORM Caching - Reduce database access. Hibernate does it using Primary Caching or support from Secondary caching like ehCache
Spring Caching - Reduce function invocation. 

##Annotations
###@EnableCaching
This annotation make the project ready for caching functionality
###@Cacheable
Prevent re-invocation of same function with same parameter

###Code Details
* getBookByISBN - returns new book for first time & returns the same allocated book for next time onwards.