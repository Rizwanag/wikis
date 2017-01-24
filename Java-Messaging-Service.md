###Introduction
JMS is an API that provides the facility to create, send & read messages. It provides loosely coupled, reliable & asynchronous communication.

* Technique to communicate application or software components
* Used to send message from one application to another

###Advantages of JMS
* Async - Client will receive message automatically without any pull request. As soon as the message come & client is registered to the server, the client will receive message.
* Reliable - This framework ensures that the message will be delivered to right destination. 

###Two types of messaging

* Point to Point
  - Queue based
  - Message is delivered to one receiver only. 
  - Queue is used for infrastructure to hold message. 

* Publisher-Subscriber, Topic 
  - Messages are hold & delivered. 
  - One message is delivered to subscribers and thus, it is like broadcasting. 

###Dependencies

     <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-activemq</artifactId>
     </dependency>
     <dependency>
            <groupId>org.apache.activemq</groupId>
            <artifactId>activemq-broker</artifactId>
     </dependency>
     <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
     </dependency>

##Steps

###Application.java
* @EnableJMS on the Application class. Because of 
* Bean creations
  - Endpoint Listener Container creation.
  - Converting Text to JSon. This bean serializes object to JSON.

###Receiver.java
* Functions are annotated with @JmsListener. It contains destination name & messaging end-point. 

