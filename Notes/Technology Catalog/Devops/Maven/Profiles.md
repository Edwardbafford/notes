
Profiles allow you to override any settings in the pom.xml for different environments.

- project
	- profiles
		- profile
			- id
			- activation
				- ...
			- ...

Execute maven with a profile: `mvn ... -P<PROFILE_NAME>`

Profiles can be defined in
- `pom.xml`
- `profiles.xml`
- `~/.m2/settings.xml`
- `${M2_HOME}/conf/settings.xml`

List all profiles: `mvn help:active-profiles`

`id` elements defines the profile name used to activate it

`activation` defines environmental condition which will automatically activate a profile without being specifically referenced.
- jdk
- os
- property
- file
- environment variables

A profile can alter anything in the pom.xml


Use different dependencies with different profiles using

- dependenct
	- classifier -> profile name