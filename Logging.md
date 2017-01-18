###Dependencies

    <dependency>
       <groupId>log4j</groupId>
       <artifactId>log4j</artifactId>
       <version>${log4j.version}</version>
    </dependency>


###log4j.properties
* Place this file in /resources
* Here, you have root logger option
* Console log option
* File log option

###Steps
* Create a log object in the class that you intend to log
final static Logger logger = Logger.getLogger(HelloExample.class);
* There are various levels associated - debug-> info-> warning-> error-> fatal

###Console Logs
log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.Target=System.out
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %m%n

###File logs
log4j.appender.file=org.apache.log4j.RollingFileAppender
log4j.appender.file.File=D:\\log4j-application.log
log4j.appender.file.MaxFileSize=5MB
log4j.appender.file.MaxBackupIndex=10
log4j.appender.file.layout=org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern=%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %m%n


###Differences between log4j & log4j2
Significant differences in reliability & performances
* http://logging.apache.org/log4j/2.x/performance.html
* http://logging.apache.org/log4j/2.x/manual/configuration.html