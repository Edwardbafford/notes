
**Builds** consist of a series of **Phases**.

Each **Phase** is linked to a series of **Goals** which are executed during the build.

**Plugins** expose maven to non-default goals and phases which can be linked to builds as needed.

Execute build: `mvn <BUILD>`

Execute goal: `mvn <PLUGIN>:<GOAL>`

Standard builds
- clean
- default (also know as build)
- site

## Build Configuration

XML Structure:
- build
	- plugins
		- plugin
			- artifactId
			- executions
				- execution
					- id
					- phase
					- goals
						- goal
					- configuration
			- dependencies

Reference new or existing plugins.

Define dependencies if needed.

Configure behavior of the plugin.

Link plugin goals to phases.


## Clean Lifecycle

`mvn clean`

Phases
- pre-clean
- clean
- post-clean

By default only `clean:clean` goal is executed which deletes the output of a build by deleting the build directory.

The build directory by default of the Super POM is `${basedir}/target`

Configure `maven-clean-plugin` to remove or not remove specific files.


## Default Lifecycle

This is the main lifecycle!

Phases can be broken down into a couple of main parts
- Validation
- Generating sources and resources
- Compiling code
- Unit Testing
- Packaging code
- Integration testing
- Further validation
- Maven installation
- Artifact deployment

Phases
- validate
- generate-sources
- process-sources
- generate-resources
- process-resources
- compile
- process-classes
- generate-test-sources
- process-test-sources
- generate-test-resources
- process-test-resources
- test-compile
- test
- prepare-package
- package
- pre-integration-test
- integration-test
- post-integration-test
- verify
- install
- deploy

The packaging element (`project.packaging`) determines the default goals.

Packaging Types
- JAR - the default
- POM - pom only project
- Maven Plugin - for building a maven plugin
- WAR - for WAR files, uses `war:war` goal during the package phase which requires a `web.xml` file

You can also create custom packages with custom goals. This requires:
- Plugin that defines the lifecycle for the custom package type
- Repository with that plugin


## Site Lifecycle

Used for documentation generation

`mvn site`

Phases and default goals
- pre-site
- site
	- site:site
- post-site
- site-deploy
	- site:deploy


## Common Functionality

### Process Resources

`resources:resources` is usually linked to the `process-resources` phase.

Copies files from `${basedir}/src/main/resources` to `${basedir}/target/classes`. 

Configure input directories/files through `project.build.resources` in POM

Configure output directory through the `project.build.outputDirectory` element.

Inject properties into resources just like with the POM
1. Use injection syntax in resources
2. Create property file
3. Reference property file with `project.build.filters.filter` in POM
4. Enable filtering in `project.build.resources.resource.directory`

### Compile

Usually uses the `compile:compile` goal.

Compiles all source code.

Copies bytecode from `${basedir}/src/main/java` to `${basedir}/target/classes`. 

Configure source directory through the `project.build.sourceDirectory` element in POM.

Configure output directory through the `project.build.outputDirectory` element in POM.

Configure compile version and JVM runtime version from within the `maven-compiler-plugin` `configuration` element using `source` and `target`

### Process Test Resources

Same as the process resources phase except for the input and output directories.

`${basedir}/src/test/resources`

`${basedir}/target/test-classes`. 

### Test Compile

Very similar to `compile` phase.

Usually uses `compile:testCompile` goal.

Copies bytecode from `${basedir}/src/test/java` to `${basedir}/target/test-classes`, which can be overriden.

References the same `maven-compiler-plugin` `source` and `target`

### Test

Usually uses the `surefire:test` goal from the `maven-surefire-plugin` plugin.

Looks for all classes ending in Test in the test source directory and runs them as JUnit tests.

It can be configured to use TestNG framework as well.

Reports are produced in the `target/surefire-reports` directory. Two files for each test:
- XML file containing execution information
- Text file with output

Ignore failures by configuring the plugin with `testFailureIgnore` to `true`

Skip tests using the command `mvn ... -Dmaven.test.skip=true`

### Install

Usually uses the `install:install` goal.

Install the project's artifact/s into the local Maven repository.

### Deploy

Usually uses the `deploy:deploy` goal.

Deploys the project's artifact/s into a remote Maven repository.