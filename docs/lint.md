## lint
### Overview
Enables the [gradle-quality-plugin](http://xvik.github.io/gradle-quality-plugin/) with the following
linters:
* [PMD](https://pmd.github.io)
* CPD (duplicate code finder)
* [SpotBugs](https://spotbugs.github.io) with [FindSecurityBugs](https://find-sec-bugs.github.io)

To open the reports in web browser use:
```shell
open build/reports/cpd/cpdCheck.html
open build/reports/pmd/main.html
open build/reports/spotbugs/main.html 
```


### Configuration
* `lint_excludes` configuration property controls which files will be excluded from the linter.
* `skipLint` configuration disables temporary the linter execution. Usage: `./gradlew clean build -PskipLint`
### Defaults
```groovy
ext {
  lint_excludes = ['com/dt/**/dto/*', 'com/dt/**/api/*']
}
```
