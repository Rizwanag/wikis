###Introduction
* It's a lightweight security framework.
* Provides authentication & authorization support.
* Secures spring based applications
* Integrates well with Spring MVC.
* Security algorithms implemented

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
* Url to view name mapping


###Configuration
* Enable the class responsible for providing web security with @EnableWebSecurity
* WebSecurity class should extend WebSecurityConfigurerAdapter
* Implement configure & configureGlobal function

###Functions
* antMatchers - Provide all the matches
* anyRequest - GET/POST
* authenticated

.formLogin()
                .loginPage("/login")
                .permitAll()
                .and()



###Notes
* Create user/password & the roles to which user belongs
* Create antMatchers & designate roles which are capable of accessing it.
* If you are trying to access pages which have permissions, you will be prompted login page
* Login Page will be prompted because of fromLogin
* Logout will be invokes by calling /logout

###Code Details for adding Security
* Extend class WebSecurityConfigurerAdapter & override - configure & configureGlobal
* configureGlobal - we mention authentication & authorization information
* configure - urls & the roles which have permissions to access the urls