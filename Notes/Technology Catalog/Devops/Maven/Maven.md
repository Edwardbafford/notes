
Build software used mainly for [[Java]] projects

Installation only depends on Java runtime

`~/.m2`
- settings.xml - user specific config options
- repository - local repository to house dependencies

pom.xml - stands for Project Object Model and is the declarative configuration for a maven project


# POM


## Project Coordinates

Used to identify a project and are mandatory within the pom file.

- project
	- groupId - used for creating hierarchical groups within repositories
	- artifactId - main id for a project, group + artifact id must be unique
	- version - used for versioning project

Version format: `<major>.<minor>.<increment>-<qualifier>`

### Snapshots

`SNAPSHOT` can be used as a version qualifier and will cause
- Uploads to append a date and time
- Uploads must be to a snapshot repository


## Properties

Reference properties within the pom using: `${...}`

Dot path notation is used to reference the property

Secrets should be stored in you settings.xml and not checked into version control.

Pass environment variables into a maven build: `mvn ... -Denvironment....=...`

### Types

Environment variables -> `${env.VAR_NAME}`

Elements within the pom.xml file -> `${project....}`

Elements within the settings.xml file -> `${settings....}`

Java properties that are accessible through `system.getProperties()` are directly referenced -> `${...}`

Properties specifically defined within the properties element of the pom.xml are directly referenced -> `${...}`


## Dependencies

pom format:
 - project
	 - dependencies
		 - dependency
			 - groupId
			 - artifactId
			 - version
			 - scope
			 - optional
			 - exclusions
				 - exclude
					 - groupId
					 - artifactId

Dependencies defines the list of artifacts to include with the project

Each dependency is referenced using its project coordinate

versions can be ranged between two values to add flexibility to the maven build program
- (,) - exclusive
- \[,\] - inclusive

scopes define where the dependency should be included
- `compile` is the default and makes it available in all classpaths
- `provided` makes it available at compile time but not at runtime, where it must be provided by the environment
- `test` makes it available at compile and runtime but only in the testing stages of the build

optional field is either true or false with false being the default. If true the dependency will not be transitively included in other projects

**Transitive dependencies** are dependencies of a dependency. These are automatically added by Maven.

Exclusions field can be used to exclude transitive dependencies.


## Project Inheritance

Parent poms are used as a starting point for lower level pom.xml files.

If no parents are explicitly referenced then the Super POM is used as the parent implicitly.

- project
	- parent
		- coordinates
		- relativePath

Maven reads parent from
- Local repository
- Parent directory (../pom.xml)
- Path defined by the relativePath field

View fully compiled pom: `mvn help:effective-pom`

### Super POM

Defines
- default Repository
- default plugin repository, plugins, and versions
- project structure defaults

### Dependency Management

- project
	- dependencyManagement
		- dependencies

Define dependencies that child poms will use as defaults

Child poms reference group and artifact Ids of dependencies and the rest of the configuration is inherited by parent


