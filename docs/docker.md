## docker
### Overview
Uses [jib](https://github.com/GoogleContainerTools/jib) to package the application as docker image.
It is configured to use Amazon Corretto 17 as Java runtime


### Configuration
The following docker environment variables are available:
* `SPRING_PROFILES_ACTIVE` - changes the Spring configuration profile
* `DT_DB_SCHEMA` - this and the properties below are used to configure the DB access
* `DT_DB_URL`
* `DT_DB_USERNAME`
* `DT_DB_PASSWORD`

Additionally, you can use the standard environment variables supported by Java executable:
* [JDK_JAVA_OPTIONS](https://docs.oracle.com/en/java/javase/17/docs/specs/man/java.html#using-the-jdk_java_options-launcher-environment-variable)
* [JAVA_TOOL_OPTIONS](https://docs.oracle.com/en/java/javase/17/docs/specs/jvmti.html#tooloptions)
* `CLASSPATH`
* `JAVA_HOME`


### Defaults
```properties
SPRING_PROFILES_ACTIVE: "default",
DT_DB_SCHEMA: "public",
DT_DB_URL: "jdbc:postgresql://localhost:5432/postgres?currentSchema=\${DT_DB_SCHEMA}",
DT_DB_USERNAME: "postgres",
DT_DB_PASSWORD: "postgres"
```
