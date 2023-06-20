
Set of practices, tools, and cultural for automating and integrating software development and IT operational management.

**Toil** refers to tasks that need to be repeatably and manually executed by developer. Minimizing toil helps speed up development and make it more reliable.


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
- [[#Testing|test project]]
- save artifacts (optional)
- automatically send reports to developers

Technologies
- Platforms
	- Github/Gitlab
	- AWS Code commit
- [[Jenkins]]
- Circle CI


## Continuous Delivery/Deployment

Continuous delivery implies deploying an application to an environment based on a human trigger.

Continuous deployment implies deploying an application to an environment in a fully automated way.

The difference is in how the deployment is triggered.

Automating the deployment process increases reliability and delivery speed.

#### Simple Deployment

Delete old version of the application then deploy the new version.

A rollback involves deleting the new version then re-deploying the old version.

Simple but involves downtime.

Any CI tool should be able to do this.

#### Blue/Green Deployment

1. Deploy an instance of the new version without deleting the old version
2. Optionally test new deployment
3. Switch traffic from the old version to the new version
4. Delete the old version

Rollback involves re-deploying the old version and switching traffic back.

You can also slowly switch a percent of the traffic at a time for an even smoother transition and less risk, called a **Canary Deployment**

Less downtime but more complex!

You need specialized tools for this:
- Spinnaker
- Argo CI
- Circle CI
- AWS Code Deploy

#### Pull Based Deployments

Systems monitor the deployed environments and artifacts to deploy.

Complex but prevents drift.

- Flux CD


## Security

#### CI

- Language linters with failure criteria
- Static code analysis with failure criteria
	- [[SonarQube]]
- Container vulnerability scanning with failure criteria
	- [[Anchor]]
	- [[ECR]]
- Automated security tests 
- Code reviews before merge

#### CD

- CD pipelines fetch secrets from secret management system and inject them into the deployments.
	- [[HashiCorp Vault]]
	- [[AWS Secrets Manager]]
- Apply checks to what's getting deployed
	- [[Binary Authorization]] for [[Kubernetes|K8s]]

#### Manual

- Cyber Security team should regularly audit code/systems and provide feedback
- Enforce principle of least privilege with simple processes for increasing access
- Standardize operating procedures with auditing for
	- Secret management
	- Access control
	- Vulnerability testing
	- CI/CD


## GitOps

An implementation of DevOps where [[Git]] repositories are the single source of truth.
- infrastructure
- configuration
- application code

Deployment options
- Push model where commit triggers deployment
- [[#Pull Based Deployments|Pull model]] where a tool is used to monitor the environments and repositories and keeps them in sync

#### Application Repository

The application repository should store application code.

Branching strategy guidelines
- Master branch contains production releases
- Develop branch contains non-production code
- Feature branches used for developing new features and merging back into Develop branch

#### Environment Repository

The environment repository should store code related to infrastructure and configuration.

Each branch should represent the code for an environment.

Lower environment changes need to be merged into upper environments.

Higher environment changes can immediately be applied to all lower levels.


## Testing

- Unit Testing
	- Language specific frameworks
- Integration Testing
	- API
	- User Stories
- Load Testing
	- [[Apache Bench]]
- User Acceptance
- Chaos Testing
	- Chaos Monkey


## Monitoring

- CPU
- Memory
- Disk Space
- Logs

For containers
- CPU
- Throttled CPU - time throttled by container
- Memory usage
- Memory fail counters - no. of memory requests rejected by containers
- Swag - using swap is a sign of memory hungry containers
- Disk I/o
- Network metrics

- [[Prometheus]]
