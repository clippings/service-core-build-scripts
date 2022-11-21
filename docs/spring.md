## spring
### Overview

There are two Spring Boot plugins.

The first one named purely `spring` provides the default spring configuration and required
set of dependencies:
Enables Spring Boot plugin and adds the following core spring dependencies to the project:
* `spring-boot-starter` - the main Spring Boot starter
* `spring-boot-starter-validation` - Enables Java Bean validation in Spring
    * https://www.baeldung.com/javax-validation
    * https://www.baeldung.com/javax-validation-method-constraints
* `spring-boot-starter-web` - enables traditional (non-reactive) web server and rest api development
    * https://spring.io/guides/tutorials/rest/
* `spring-boot-starter-actuator` - out-of-the-box implementation for cross-cutting-concerns. Enables
  monitoring, health checks, diagnostics endpoints, and on the fly configuration.
    * https://spring.io/guides/gs/actuator-service/
    * https://www.baeldung.com/spring-boot-actuators

Open Telemetry (Monitoring) Dependencies:
* `spring-cloud-sleuth-otel-dependencies` - to include spring cloud sleuth OTEL dependencies
* `opentelemetry-exporter-otlp` - to include open telemetry exporter to send trace data .
* `micrometer-registry-prometheus` - to enable prometheus-ready metrics

Some additional dependencies:
* `logstash-logback-encoder` - the log formatter, that we use to enable [JSON logging](https://github.com/logfellow/logstash-logback-encoder)
* `json-patch` - an RFC 6902 (JSON Patch) and reverse, plus RFC 7386 (JSON Merge Patch),
  implementation in Java
* [spring-boot-devtools](https://docs.spring.io/spring-boot/docs/current/reference/html/using.html#using.devtools)

For testing we add:
* `spring-boot-starter-test` - that adds capabilities to create Spring unit and integration tests,
  based on [jUnit 5 (Jupiter)](https://junit.org/junit5/docs/current/user-guide/) platform.
* `testcontainers` - version management bom
* `spring-cloud` - version management bom

The second plugin named `spring-db` adds dependencies, to enable your application to use
databases, in particular PostgreSQL:
* `spring-boot-starter-data-jpa` - DB access, using JPA/Hibernate
* `postgresql` - database driver & test container
* `liquibase` - the tool we use for automatic DB migrations
* `datasource-proxy-spring-boot-starter` - to properly
  [format the SQL queries](https://vladmihalcea.com/log-sql-spring-boot/), when debug is enabled.

You shouldn't use the `spring-db` plugin alone. Import the `spring` plugin first.

The reason for having a separate `spring-db` plugin is that it is very possible, that some
microservices don't need DB support.

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


### Version Management
Majority of the versions are managed by spring itself by properties, that typically look like
`<package>.version`. You can check out the [dependencies
managed by Spring](https://docs.spring.io/spring-boot/docs/current/reference/html/dependency-versions.html#appendix.dependency-versions.properties):

Have in mind, that Spring manages the dependencies version. You still need to add the library
to your dependencies, but it is not necessary to specify its version.

If you would like to update the version of that dependency, simply edit your `gradle.properties`
and add the required property with the new, upgraded version.

We are defining the following version properties:

| Property                         | Default Value |
|----------------------------------|---------------|
| logstash-logback-encoder.version | 7.2           |
| json-patch.version               | 1.13          |
| datasource-proxy.version         | 1.8.0         |
| testcontainers.version           | 1.17.3        |
| spring-cloud.version             | 2021.0.4      |
| spring-cloud-sleuth-otel.version | 1.1.0         |
| map-struct.version               | 1.5.3.Final   |


### References
* MapStruct
  * https://www.baeldung.com/mapstruct
  * https://medium.com/uphill-engineering-design/deep-dive-into-mapstruct-spring-7ddd8dac3d6d
  * https://github.com/mapstruct/mapstruct-examples
* JsonPatch
  * https://jsonpatch.com
  * https://www.baeldung.com/spring-rest-json-patch
  * https://cassiomolin.com/2019/06/10/using-http-patch-in-spring/
  * https://github.com/omlip/json-patch-example
  * https://bijukunjummen.medium.com/json-patch-and-json-merge-patch-quick-example-in-java-c36fdabc2810
  * https://docs.spring.io/spring-data/rest/docs/current/api/org/springframework/data/rest/webmvc/json/patch/package-summary.html
* Spring Cloud Sleuth
  * https://spring.io/projects/spring-cloud-sleuth
  * https://www.baeldung.com/spring-cloud-sleuth-single-application
  * https://opentelemetry.io
* TestContainers
  * https://www.testcontainers.org
  * https://www.baeldung.com/spring-boot-testcontainers-integration-test
  * https://www.baeldung.com/docker-test-containers
  * https://www.baeldung.com/spring-boot-redis-testcontainers
  * https://www.baeldung.com/spring-dynamicpropertysource
