
Set of practices, tools, and cultural for automating and integrating software development and IT operational management.

## Patterns

**Version control** - manage all your code in a way that prevents loss of any data.

**Infrastructure as code** - define your infrastructure as code that can be versioned.

**Configuration as code** - define the configuration process for your infrastructure as code that can be versioned.

**Immutable Infrastructure** - create snapshot artifacts of your configured infrastructure for easy re-use and deployment.


## Technologies

- [[Git]] for version control
- [[Terraform]] for infrastructure as code
- [[Ansible]] for configuration as code
- [[Packer]] for building immutable infrastructure with VM snapshots
- [[Docker]] for simplifying the build, test, and deploy processes
* [[Prometheus]] for monitoring
* [[Apache Bench]] for load testing


## CI/CD

Continuous Integration - test code as it's updated

Continuous Development - automate the deployment process

Basic Flow
1. Code is stored in a Repository and updated
2. Commits to important branches trigger the following process
	1. Build from source code
	2. Test source code
	3. Save artifacts
3. When deploying reference an environment and version to automate




## Monitoring

- CPU
- Memory
- Disk Space

For containers
- CPU
- Throttled CPU - time throttled by container
- Memory usage
- Memory fail counters - no. of memory requests rejected by containers
- Swag - using swap is a sign of memory hungry containers
- Disk I/o
- Network metrics

