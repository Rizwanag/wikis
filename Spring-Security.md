###Introduction
* It's a lightweight security framework - Authentication + Authorization.
* Provides authentication & authorization support.
* Secures spring based applications
* Integrates well with Spring MVC.
* Best Security algorithms implemented by default.

###Dependencies

    <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>
        <!-- tag::security[] -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-security</artifactId>
        </dependency>
        <!-- end::security[] -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-test</artifactId>
            <scope>test</scope>
        </dependency>


###Configuration
* Url to view name mapping.
* Achieved by extending WebMvcConfigurerAdapter.
* Implement addViewControllers - Do the mapping of url to view name.
* Spring Boot is creating the bean & injecting here. 


###Configuration to add security to web mvc project
* Enable the class responsible for providing web security with @EnableWebSecurity
* WebSecurity class should extend WebSecurityConfigurerAdapter
* Implement configure & configureGlobal function
* configure() will have all rules of authentication & authorization 
* configureGlobal() will have user/password/role rule

###Functions
All the below checks are happening for the logged in user.
* antMatchers - Provide all the matches
* anyRequest - GET/POST
* authenticated - allowed a user with hasRole() to access urls in antMatchers
* hasRole - You provide roles that you want to allow for the antmatchers
* permitAll - allow all roles for this antmatchers
* fromLogin - If any of the user is not sufficiently authenticated, the application prompts to login page.
* loginPage - Mention the url containing login page here. And, web application will be redirected to this if auth is not sufficient. 
  
.formLogin()
                .loginPage("/login")
                .permitAll()
                .and()



###Steps of adding security
* Create user/password & the roles to which user belongs
* Create antMatchers & designate roles which are capable of accessing it.
* If you are trying to access pages which have permissions, you will be prompted login page
* Login Page will be prompted because of fromLogin()
* Logout will be invokes by calling /logout or it is also configurable

###Code Details for adding Security
* Extend class WebSecurityConfigurerAdapter & override - configure & configureGlobal
* configureGlobal - we mention authentication & authorization information
* configure - urls & the roles which have permissions to access the urls

Spring Security chooses the best algorithm for the application.