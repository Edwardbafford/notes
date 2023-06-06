
Set of practices, tools, and cultural for automating and integrating software development and IT operational management.

Continuous Integration - test code as it's updated

Continuous Development - automate the deployment process

Basic Flow
1. Code is stored in a Repository and updated
2. Commits to important branches trigger the following process
	1. Build from source code
	2. Test source code
	3. Save artifacts
3. When deploying reference an environment and version to automate


## Technologies
- [[Git]] for version control
- [[Terraform]] for infrastructure as code
- [[Ansible]] for configuration as code
- [[Docker]] for simplifying the build, test, and deploy processes
* [[Prometheus]] for monitoring
* [[Apache Bench]] for load testing


## IaC

Infrastructure as code

Use code to define infrastructure

Features
- Declarative
- Idempotent
- Repeatable
- Version controlled


## CaC

Configuration as code

Manage configurations through code

Features
- Declarative
- Idempotent
- Repeatable
- Version controlled


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

