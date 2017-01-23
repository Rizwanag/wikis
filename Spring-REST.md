Spring server can be easily integrated with REST infrastructure. Server exposes REST API's using which other client's or server can talk to it. Data is predominantly passed in JSON format.

###@RestController
* The controller becomes ready now to return objects.
* The objects are now converted to json before sending to client

###Dependencies
 <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>com.jayway.jsonpath</groupId>
            <artifactId>json-path</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

* Each rest function returns an object, 