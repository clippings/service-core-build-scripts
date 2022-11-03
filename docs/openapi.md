## openapi
### Overview
Uses the [OpenAPI Generator](https://openapi-generator.tech) to generate Spring-MVC server stubs
and DTO files out of OpenAPI specification file.

It will generate the files in `build/generated/api` folder, and will use the following Java
packages, for the generated files:
* `com.dt.${project.name}.api` - contains Rest Controller interfaces for endpoints specified
  in `paths` section of the specification, split by tags. Enables Java Bean Validation.
* `com.dt.${project.name}.dto` - contains the DTOs generated from the `schema` section.


### Configuration
* `serverOpenApiFile` is the path to the OpenAPI specification file. You can set this property
  in `gradle.properties`. If it is not set, the OpenAPI generator will not be invoked.
* With `serverOpenApiPackage` you can control the base package name of the generated code.
  It defaults to `com.dt.<project-name>`.

### Defaults
There is no default configuration.
