## spring
### Overview
Enables Spring Boot plugin and adds the following core spring dependencies to the project:
* `spring-boot-starter` - the main Spring Boot starter
* `spring-boot-starter-data-jpa` - DB access, using JPA/Hibernate
* `spring-boot-starter-validation` - Enables Java Bean validation in Spring
    * https://www.baeldung.com/javax-validation
    * https://www.baeldung.com/javax-validation-method-constraints
* `spring-boot-starter-web` - enables traditional (non-reactive) web server and rest api development
    * https://spring.io/guides/tutorials/rest/
* `spring-boot-starter-actuator` - out-of-the-box implementation for cross-cutting-concerns. Enables
  monitoring, health checks, diagnostics endpoints, and on the fly configuration.
    * https://spring.io/guides/gs/actuator-service/
    * https://www.baeldung.com/spring-boot-actuators

Some additional dependencies:
* `datasource-proxy-spring-boot-starter` - to properly format the SQL queries, when debug is enabled.
* `postgresql` - our database driver
* `liquibase` - the tool we use for automatic DB migrations
* `logstash-logback-encoder` - the log formatter, that we use to enable JSON logging
* `json-patch` - an RFC 6902 (JSON Patch) and reverse, plus RFC 7386 (JSON Merge Patch),
  implementation in Java
* [spring-boot-devtools](https://docs.spring.io/spring-boot/docs/current/reference/html/using.html#using.devtools)

For testing we add:
* `spring-boot-starter-test` - that adds capabilities to create Spring unit and integration tests,
  based on [jUnit 5 (Jupiter)](https://junit.org/junit5/docs/current/user-guide/) platform.
* `testcontainers` - will automatically start a PostgreSQL in docker container during testing


### Configuration
* `skipTest` configuration disables temporary the test execution.
  Usage: `./gradlew clean build -PskipTest`

### Defaults
By default, when running `./gradlew bootRun` it is started with argument
`--spring.profiles.active=dev`. To override this behaviour use something like:

```groovy
bootRun {
    args = [ '--spring.profiles.active=prod' ]
}
```
