## formatter
### Overview
Enables the [Spotless](https://github.com/diffplug/spotless) plugin, that will automatically
reformat the code according the following rules:
* Java files are formatted with [Google Java Format](https://github.com/google/google-java-format),
  and the following rules:
    * removeUnusedImports
    * importOrder
    * trimTrailingWhitespace
    * indentWithSpaces
    * endWithNewline
    * formatAnnotations
    * and default licenseHeader
* Gradle files are formatted with eclipse groovy formatter
* Markdown, XML, YAML files are formatted with rules:
    * trimTrailingWhitespace
    * endWithNewline

