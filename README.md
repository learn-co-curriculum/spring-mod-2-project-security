# Project Work Time - Security

## Learning Goals

- Spend some time working on your project.

## Project Work Time

Now that we have learned a little more about Spring Security, it's time to apply
this new knowledge to our projects!

Modify the project to include the spring security dependency in the `pom.xml`:

```xml
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-security</artifactId>
        </dependency>
```

Consider the following instructions:

- Add a new package under the `com.example.springproject` package called
  `config`.
- Create a class called `SecurityConfiguration` under the `config` class.
- Create a `filterChain()` bean method that requires all endpoints to be
  authenticated, as we saw in previous lessons.
- Within the `filterChain()` method, add a line that looks like this:
  `httpSecurity.csrf().disable();`
  - When it comes to POST, PUT, AND DELETE requests, Spring Security (by
    default) will require a CSRF token. For our project, we will disable this
    protection, but know that this should be enabled in an actual production
    environment. Knowledge of implementing a CSRF token is out of scope for this
    module.
- When you start up the application, you should see an auto-generated user
  password. Use that password and the default username `user` to test the
  endpoints using Postman.

Refer back to the Security Introduction lesson to help you walk through how to
test the endpoints along with the Authentication lesson in setting up the
`SecurityConfiguration` class.

## Stretch Goals

There are quite a few stretch goals regarding Spring Security. You may choose to
implement these if time allows. We recommend implementing these stretch goals in
the following order:

- Implement authentication with the campers' credentials.
- Implement authorization so that the camper logged in can only access his or
  her signups.

For the first stretch goal: "implement authentication with the campers'
credentials", use the username and password that each camper has associated with
them in order to provide HTTP basic auth to the application. See the
Authentication Code-Along and instead of a `User` entity, we would use the
`Camper` entity. We would also permit-all on the POST methods if we choose to
implement this stretch goal.

The second stretch goal: "implement authorization so that the camper logged
in can only access his or her signups" is an extension to the first stretch goal
and should be implemented _only_ if the first stretch goal has been implemented.
This would require adding authorities to the `Camper` entity and a couple of
extra tables to be added to the `camp_db` database. See the Authorization
Code-Along as a reference in how to implement this stretch goal.

> Note it is **not** required to implement either of these stretch goals. They
> exist for students who want more of a challenge.

## Resources

- [Spring Security Fundamentals - Lesson 1 - First Steps](https://www.youtube.com/watch?v=nSu9ElsnNtY&list=PLEocw3gLFc8X_a8hGWGaBnSkPFJmbb8QP)
- [Spring Security in Action](https://learning.oreilly.com/library/view/spring-security-in/9781617297731/OEBPS/Text/02.htm#heading_id_7)
- [UserDetailsService Documentation](https://docs.spring.io/spring-security/site/docs/current/api/org/springframework/security/core/userdetails/UserDetailsService.html)
- [InMemoryUserDetailsManager Documentation](https://docs.spring.io/spring-security/site/docs/current/api/org/springframework/security/provisioning/InMemoryUserDetailsManager.html)
- [PasswordEncoder Documentation](https://docs.spring.io/spring-security/reference/servlet/authentication/passwords/password-encoder.html)
- [Spring Security Fundamentals - Lesson 2 - Managing Users](https://youtu.be/dFvbHZ8CuKM)
- [Spring Security: Authentication with a Database-backed UserDetailsService](https://www.baeldung.com/spring-security-authentication-with-a-database)
- [Spring Security without the WebSecurityConfigurerAdapter](https://spring.io/blog/2022/02/21/spring-security-without-the-websecurityconfigureradapter)
- [HttpSecurity Documentation](https://docs.spring.io/spring-security/site/docs/current/api/org/springframework/security/config/annotation/web/builders/HttpSecurity.html)
- [Spring Security - security none, filters none, access permitAll](https://www.baeldung.com/security-none-filters-none-access-permitAll)
- [Baeldung: Granted Authority Versus Role in Spring Security](https://www.baeldung.com/spring-security-granted-authority-vs-role)
- [Entity Mappings: Introduction to JPA Fetch Types](https://thorben-janssen.com/entity-mappings-introduction-jpa-fetchtypes/#FetchTypeEAGER_8211_Fetch_it_so_you8217ll_have_it_when_you_need_it)
- [Hibernate Bidirectional Mapping Example with @JoinTable Annotation](https://www.concretepage.com/hibernate/hibernate-bidirectional-mapping-example-with-jointable-annotation)
- [BezKoder: Spring Boot, Spring Security, PostgreSQL: JWT Authentication Example](https://www.bezkoder.com/spring-boot-security-postgresql-jwt-authentication/)
