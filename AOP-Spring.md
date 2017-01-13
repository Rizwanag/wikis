http://docs.spring.io/spring/docs/current/spring-framework-reference/html/aop.html

###Spring AOP Overview
* Cross cutting concerns - logging, security, transaction etc. Functionalities which are not business specific but spans across all business modules.  
* The main purpose of AOP is that you don't pollute the business logic code. We keep the cross-cutting concerns in separate classes also known as aspect classes - Logger Classes, Security Classes.
* Objects/Beans need to be created from Spring container for AOP to get into action.

Spring AOP takes out the direct dependency of cross-cutting tasks from classes that we can’t achieve through normal object 
oriented programming model. For example, we can have a separate class for logging but again the functional classes will 
have to call these methods to achieve logging across the application.

###How is Spring AOP achieved?
Spring creates a proxy object which envelops around Business Object and Aspect ( Cross cutting concerns - logging )
Proxy Object -> Employee Object + Logging

For annotation based AOP, the AppConfig class should be annotated with @Configuration @EnableAutoJProxy for creating business beans & aspect beans.

##Aspect Oriented Programming Core Concepts
Before we dive into implementation of Spring AOP implementation, we should understand the core concepts of AOP.

###Aspect
An aspect is a class that implements enterprise application concerns that cut across multiple classes, 
such as transaction management, logging & security. Aspects can be a normal class configured through Spring XML configuration or we can use Spring AspectJ integration to define a class as Aspect using @Aspect annotation.

###Join Point
A join point is the specific point in the application such as method execution, exception handling, 
changing object variable values etc. In Spring AOP, a join points is always the execution of a method or function call.

###Advice
Advices are actions taken for a particular join point. In terms of programming, they are methods that 
gets executed when a certain join point with matching pointcut is reached in the application.Function that executes on reaching join point.

###Pointcut
Pointcut are expressions that is matched with join points to determine whether advice needs to be executed 
or not. Pointcut uses different kinds of expressions that are matched with the join points and Spring framework 
uses the AspectJ pointcut expression language.

###Target Object
They are the object on which advice's are applied. Spring AOP is implemented using runtime proxies 
so this object is always a proxied object. What is means is that a subclass is created at runtime where the target 
method is overridden and advices are included based on their configuration.

###AOP proxy
Spring AOP implementation uses JDK dynamic proxy to create the Proxy classes with target classes and 
advice invocations, these are called AOP proxy classes.

###Weaving
It is the process of linking aspects with other objects to create the advised proxy objects. This can be done 
at compile time, load time or at runtime. Spring AOP performs weaving at the runtime. Connecting the advices to a joint-point function. 


##AOP Advice Types

Based on the execution strategy of advices, they are of following types.

###@Before Advice: 
These advices runs before the execution of join point methods. We can use @Before annotation to mark 
an advice type as Before advice.

###@After (finally) Advice: 
An advice that gets executed after the join point method finishes executing, whether normally 
or by throwing an exception. We can create after advice using @After annotation.

###@After Returning Advice: 
Sometimes we want advice methods to execute only if the join point method executes normally. 
We can use @AfterReturning annotation to mark a method as after returning advice.

###@After Throwing Advice: 
This advice gets executed only when join point method throws exception, we can use it to rollback 
the transaction declaratively. We use @AfterThrowing annotation for this type of advice.

###@Around Advice: 
This is the most important and powerful advice. This advice surrounds the join point method and we can 
also choose whether to execute the join point method or not. We can write advice code that gets executed before and 
after the execution of the join point method. It is the responsibility of around advice to invoke the join point 
method and return values if the method is returning something. We use @Around annotation to create around advice methods.
