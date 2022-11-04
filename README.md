# Gradle Build Scripts

## How it works?
The Gradle build scripts are based on [Blowdryer](https://github.com/diffplug/blowdryer) 
Gradle plugin. It allows to load shared files from different locations - local file, github,
gitlab or bitbucket.

### Usage

In your `settings.gradle` you have to do something like that:
```gradle
plugins {
  id 'com.diffplug.blowdryerSetup' version '1.6.0'
}

blowdryerSetup {
  github('clippings/microservices-core', 'tag', 'v1.4.5')
}
```

In you `build.gradle` you can import the shared build files:
```gradle
plugins {
	id 'jacoco'
	id 'com.diffplug.blowdryer'
}

apply from: 干.file('java.gradle')
apply from: 干.file('formatter.gradle')
apply from: 干.file('lint.gradle')
apply from: 干.file('coverage.gradle')
apply from: 干.file('spring.gradle')
apply from: 干.file('spring-db.gradle')
apply from: 干.file('openapi.gradle')
apply from: 干.file('docker.gradle')
```

### Version Management

**Managing Plugin Versions**

The share build scripts are providing only configuration to some plugins. Even if you include the
shared script, you still need to enable the plugin. And you can combine that with gradle plugin
managements mechanism. To do so, in your `settings.gradle` add:
```groovy
pluginManagement {
	plugins {
		id 'com.diffplug.blowdryer'                 version '1.6.0'
		id 'com.diffplug.blowdryerSetup'            version '1.6.0'
		id "com.diffplug.spotless"                  version "6.11.0"
		id 'de.aaschmid.cpd'                        version '3.3'
		id 'ru.vyarus.quality'                      version '4.8.0'
		id "io.freefair.lombok"                     version "6.5.1"
		id "org.openapi.generator"                  version "6.1.0"
		id 'org.springframework.boot'               version '2.7.5'
		id 'io.spring.dependency-management'        version '1.0.15.RELEASE'
		id 'com.google.cloud.tools.jib'             version '3.3.0'
	}
}


plugins {
	id 'com.diffplug.blowdryerSetup'
	id 'com.diffplug.spotless'                      apply false
	id 'de.aaschmid.cpd'                            apply false
	id 'ru.vyarus.quality'                          apply false
	id "io.freefair.lombok"                         apply false
	id 'org.springframework.boot'                   apply false
	id "org.openapi.generator"                      apply false
	id "com.google.cloud.tools.jib"                 apply false
}
```

Have in mind, that `org.springframework.boot` version of the plugin, will install exactly the
same version of Spring Boot. So if you are looking to upgrade it, change the version of the plugin.

**Managing Dependencies Versions**

By default, the `spring` and `openapi` plugins will add some dependencies. You can uncomment the 
following lines in `gradle.properties` and set the desired version.
```properties
#jackson_databind_nullable.version = 0.2.3
#logstash_logback_encoder.version = 7.2
#json_patch.version = 1.13
#datasource_proxy.version = 1.8.0
#testcontainers.version = 1.17.3
```


### Gradle Tips & Tricks

* Run `./gradlew assemble --dry-run` to show the order how the tasks are executed.
* Run `./gradlew tasks --all` to show list of available tasks, grouped by plugin
* Run `./gradlew -q dependencies --configuration productionRuntimeClasspath` to show tree of
  dependencies consumed by your project


# Plugins

* [java](docs/java.md)
* [lint](docs/lint.md)
* [formatter](docs/formatter.md)
* [coverage](docs/coverage.md)
* [spring](docs/spring.md) and `spring-db`
* [docker](docs/docker.md)
* [openapi](docs/openapi.md)
