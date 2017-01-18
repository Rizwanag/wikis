Frameworks running on top of JUnit - HttpUnit, ServletUnit, JSFUnit, JWebUnit

###Setting up JUnit
* Add JUnit dependency in pom.xml

    <dependency>
	<groupId>junit</groupId>
        <artifactId>junit</artifactId>
	<version>4.12</version>
    </dependency>

##Annotations in Test Class
###@Test
These are the testcases to be executed

###@BeforeClass
These are the functions to be executed before any test cases of the class gets executed

###@AfterClass
These are the functions to be executed after all the test cases of the class gets executed

###@Before
This function will be executed before every test case of the class

###@After
This function will be executed after every test case of class 

##Note:
* BeforeClass,AfterClass function gets executed once for each class.
* Before,After function gets executed once for each function
* In the test case class, we create object of test-intended class
* assertEquals - tests if two values are same
* Test can have two arguments - expected, timeout

###Parameterized Test Cases
* It is used to test functions that take arguments
* You have collections of parameters defined & parameters should be annotated with @Parameters
* Number of objects that get created for this case is same as number of elements in collection
* The test case will be executed as many number of times collection elements are there
* Creates separate objects for each parameters so, information propagation won't happen between test cases.

##RunWith
When a class is annotated with RunWith or extends a class with @RunWith, JUnit will invoke associated class to run test cases.

###Categorized Test Cases


###SuitTest Cases