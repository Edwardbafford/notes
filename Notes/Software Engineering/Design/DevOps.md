
Set of practices, tools, and cultural for automating and integrating software development and IT operational management.


## Version Control

System for tracking all version of a code base so that nothing is very lost.

Everything should be managed through version control.

- [[Git]]


## Infrastructure as Code

Manage applications infrastructure as code so that changes to the infrastructure can be tracked and versioned through a VCS.

- [[Terraform]]
- [[CloudFormation]]


## Configuration as Code

Logic for configuring infrastructure should be managed as code so that changes to the infrastructure configuration can be tracked and versioned through a VCS.

- [[Ansible]]
- Chef
- Puppet

Configuration as code can be combined with infrastructure as code to product machine images through [[Packer]]


## Continuous Integration

About continuously testing code as it's updated

Post-commit and post-merge
- build project
- test project
- save artifacts (optional)
- automatically send reports to developers

Technologies
- Platforms
	- Github/Gitlab
	- AWS Code commit
- [[Jenkins]]
- Circle CI


## Testing

- Unit Testing
	- Language specific frameworks
- Integration Testing
	- API
	- User Stories
	- Security Vulnerabilities
- Load Testing
	- [[Apache Bench]]
- User Acceptance


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

Tools
- [[Prometheus]]
