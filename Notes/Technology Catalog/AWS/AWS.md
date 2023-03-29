
# Infrastructure

- Region
- Availability Zone
- Edge Location

Services and features are usually scoped by Region of Availability Zone with some being Global.

Regions are made of 3-6 availability zones which are connected with high performance netowrks for high availability of their services.

Regions to use can be chosen based on
- compliance
- proximity
- services available
- cost of services

Availability Zones are made up of one of more datacenters.

Edge Locations are uset to help deliver low latency content in extra locations.


# Access

AWS access is managed through the [[IAM]] service.

Interact with AWS via:

- Management console
- Command Line Interface
- Software Development Kit
- [[HTTP]] Requests

Management console can be logged into using username and password.

CLI, SDK, or Requests use management keys which must be created through the console.


# Services

## Access

- [[IAM]]

## Networking

- [[Route 53]]
- [[ELB]]

## Compute

- [[EC2]]

## Storage

- [[EC2 Instance Store]]
- [[EBS]]
- [[EFS]]

### Database

- [[RDS]]
- [[Aurora]]
- [[ElastiCache]]

### Devops

- [[Elastic Beanstalk]]
