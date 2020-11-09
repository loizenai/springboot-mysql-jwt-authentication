# SpringBoot Token Based Authentication Example – MySQL + JWT+ Spring JPA + RestAPIs

Tutorial Link: [SpringBoot Token Based Authentication Example](https://loizenai.com/spring-boot-security-jwt-token-bsed-authentication-example-mysql-spring-jpa-restapis/)

![SpringBoot Token Based Authentication Example](https://loizenai.com/wp-content/uploads/2020/05/Spring-Boot-Security-JWT-Token-Based-Authentication-Example-MySQL-Spring-JPA-RestAPIs.png)

“How to build SpringBoot Token Based Authentication Example?” is one of the most common questions for Java development world. So in the tutorial, I will introduce how to build it with clearly architecture and coding examples.

## Video Guide

[![Video guide SpringBoot JWT authentication](https://img.youtube.com/vi/opd2tYTsDDI/0.jpg)](https://www.youtube.com/watch?v=opd2tYTsDDI)

## Spring Security JWT Architecture – Springboot Token Based Authentication Example

This is diagram for Spring Security/JWT (Springboot Token Based Authentication Example) classes that are separated into 3 layers:
– HTTP
– Spring Security
– REST API

![Spring Security JWT Architecture](https://loizenai.com/wp-content/uploads/2020/05/Spring-Security-Jwt-Authentication-Architecture-Diagram.png)

Look at the diagram above, we can easily associate these components with Spring Security Authentication process: receive HTTP request, filter, authenticate, store Authentication data, generate token, get User details, authorize, handle exception…

At a glance:
– SecurityContextHolder provides access to the SecurityContext.
– SecurityContext holds the Authentication and possibly request-specific security information.
– Authentication represents the principal which includes GrantedAuthority that reflects the application-wide permissions granted to a principal.
– UserDetails contains necessary information to build an Authentication object from DAOs or other source of security data.
– UserDetailsService helps to create a UserDetails from a String-based username and is usually used by AuthenticationProvider.
– JwtAuthTokenFilter (extends OncePerRequestFilter) pre-processes HTTP request, from Token, create Authentication and populate it to SecurityContext.
– JwtProvider validates, parses token String or generates token String from UserDetails.
– UsernamePasswordAuthenticationToken gets username/password from login Request and combines into an instance of Authentication interface.
– AuthenticationManager uses DaoAuthenticationProvider (with help of UserDetailsService & PasswordEncoder) to validate instance of UsernamePasswordAuthenticationToken, then returns a fully populated Authentication instance on successful authentication.
– SecurityContext is established by calling SecurityContextHolder.getContext().setAuthentication(…​) with returned authentication object above.
– AuthenticationEntryPoint handles AuthenticationException.
– Access to Restful API is protected by HTTPSecurity and authorized with Method Security Expressions.

## PROJECT STRUCTURE FOR SPRINGBOOT TOKEN BASED AUTHENTICATION EXAMPLE

![SPRINGBOOT TOKEN BASED AUTHENTICATION EXAMPLE](https://loizenai.com/wp-content/uploads/2020/05/Springboot-Jwt-Authentication-Project-Structure.png)

– model package defines 2 entities User & Role that have many-to-many relationship:

![Springboot Restapi Jwt Json Web Token Authentication Many To Many User-Role](https://loizenai.com/wp-content/uploads/2020/05/Springboot-Restapi-Jwt-Json-Web-Token-Authentication-Many-To-Many-User-Role.png)

– repository package contains interfaces that use Hibernate JPA to store/retrieve data from MySQL database.
– controller package defines RestAPIs for user signup/signin and testing protected resources that is secured with JWT.
– message package defines payload data transferred from user agents (Browser/RestClient…) to RestAPIs and message back.
– security package is the main part of the project that implements JWT security.

## GOAL
In the tutorial “Springboot Token Based Authentication Example”, we expose 2 RestAPIs to signup and signin:

![Springboot Jwt Authentication – Register User Phrase](https://loizenai.com/wp-content/uploads/2020/05/springboot-jwt-authentication-register-user-phrase-jack-user.png)

## Related posts:

- [Angular CRUD Application with SpringBoot and MySQL/PostgreSQL RestAPIs](https://loizenai.com/angular-crud-application-with-springboot-and-mysql-postgresql-restapis-fullstack-angular-httpclient-post-get-put-delete/)
- [SpringBoot Upload Download Multiple Files Examples with Thymeleaf](https://loizenai.com/springboot-upload-multiple-files-examples-with-thymeleaf/)
- [Build SpringBoot CRUD Application – FullStack: Frontend (Bootstrap and Ajax) to Backend (SpringBoot and MySQL/PostgreSQL database)](https://loizenai.com/build-springboot-crud-application-fullstack-frontend-bootstrap-and-ajax-to-backend-springboot-and-mysql-postgresql-database/)
