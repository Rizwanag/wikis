###Twitter app account creation
* Register yourself to create account
* Four parameters that is required are as follows
  - Consumer Key
  - Consumer Secret
  - Access Token
  - Access Token Secret

###Dependencies

    <dependency>
       <groupId>org.twitter4j</groupId>
       <artifactId>twitter4j-core</artifactId>
       <version>4.0.4</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/org.twitter4j/twitter4j-stream -->
    <dependency>
       <groupId>org.twitter4j</groupId>
       <artifactId>twitter4j-stream</artifactId>
       <version>4.0.4</version>
    </dependency>

###Steps
* Creation of twitterStream object using consumer key, consumer secret, access token, access token secret.
* The connection between your application & Twitter Server is established using this.
* Next, startTwitter(). In this function, register the keywords you are interested in. Register the listener function. 
* Listener object is implementation of StatusListener interface. The onStatus() function gets executed for all matched(tweets having the keywords) tweets.
* How to add filters ? Create a query object & call twitterStream.filter(query) 
