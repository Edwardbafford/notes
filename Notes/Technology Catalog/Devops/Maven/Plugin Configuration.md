
Define configuration properties that are defined by goals within a plugin.

Override default dependency versions and add new ones
- plugin
	- dependencies

Set a plugin parameter for all goals
- plugin
	- configuration

Set a plugin parameter for specific executions (goal @ phase)
- plugin
	- executions
		- execution
			- phase
			- goals
				- goal
More specific override

Set parameters for goals that are executed directly from the command line by defining an execution with id "default-cli"

Customize the default behavior of a goal that is bound to the lifecycle by default using execution id "default-goal"

