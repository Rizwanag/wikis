Entire project is built up using annotation with no XML at all.

##Configuration

### DispatcherServlet Creation
* Extend AbstractAnnotationConfigDispatcherServletInitializer.
* Implement getRootConfigClass(). This guy returns all bean creation classes.
* Implement getServletConfigClasses(). This configures the servlet with path of component or configuration classes.
* Implement getServletMappings() to tell web server that this servlet will be invoked on which all urls.
  
### Bean Creation Class
* Have functions in this class to create beans
* @Configuration over the class make the class capable of creating beans

### Enable Spring WebMVC
* You may use the same Bean creation class to configure webmvc
* Annotate with @EnableWebMvc
* Mention the package name of the component classes ( controllers/ repository / component )
* When Spring application boots up, it create beans of all the component classes. 
* Thus, we need to mention the package where to find these component classes. 
* ConfigureViewResolver() - Set Prefix, set suffix, view class
* addResourceHandlers() - This is to add static resources. 

### Hibernate Configuration
* Annotate the class providing with hibernate configuration @Configuration
* Create beans out of the class
* The beans will be hibernate specific - Sessionfactory, DataSource, TxMgr

##Controller
* For every HttpRequest, the request message goes to controller. 
* Controller uses services for getting information from persistent storage.
* Using service beans, controller get all information from database.

##Service
* On annotating a class with @Service, Spring framework creates a bean of it.
* Controller is dependent on service class beans.
 
##Model

##DAO
* Creates bean. Service class is dependent on the bean.

##Security