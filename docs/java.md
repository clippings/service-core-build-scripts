## java
### Overview

The `java` plugin is responsible for:
* Setting the Java compiler version to 1.7, and sets UTF-8 encoding to source files.
* Enabling the [lombok](https://projectlombok.org) to add some syntax sugar and save from writing
  useless Java boilerplate code.
* Enables the [Central Maven Repository](https://search.maven.org)
* Adds our own [GitHub Package Repository](https://maven.pkg.github.com/clippings/service-core-starter)
* Configures IntelliJ IDEA to automatically download the source jars of the dependencies, so
  developers will have up-to-date documentation in their IDE.


### Configuration
If you are using packages from our GitHub package repository you may need to authenticate. To do so
you should export the following environment variables:

| Name         | Description                                                                                       |
|--------------|---------------------------------------------------------------------------------------------------|
| GITHUB_ACTOR | You github username. As example `vvalchev`                                                        |
| GITHUB_TOKEN | [A GitHub Personal Access Token](https://github.com/settings/tokens) with `read:packages` access. |
| gpr.user     | Alternative to GITHUB_ACTOR. Usage: `./gradlew build -Pgpr.user=username`                         |
| gpr.key      | Alternative to GITHUB_TOKEN. Usage same as above.                                                 |
