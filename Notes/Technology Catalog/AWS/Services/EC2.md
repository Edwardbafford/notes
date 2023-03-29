
Elastic Cloud Compute

VM as a service

**User data script** can be setup to run at first startup of instance

[[Security Group|Security groups]] control access to the instance

Naming convention
(type)(generation).(size)
m5.xlarge

IP changes on restart, use an [[Elastic IP]] and/or [[Elastic Network Inferface]] to keep constant.


## Types

- General purpose
- Compute optimized
- Memory optimized
- Storage optimized - read/write speed efficiency


## Purchasing Options

**On Demand:** Pay for time used

**Savings Plan:** Pay for a period with an instance family

**Reserved Instance:** Pay for a period with a defined instance

**Convertible Reserved Instance:** Pay for a period with added flexibility over regular reserved instance

**Spot Instance:** Set a maximum price and lose the instance if the price raises above limit

**Dedicated Host:** Dedicated server for the customer. They have complete control over it.

**Dedicated Instance:** Single VM on a server for security purposes.

**Capacity Reservation:** Reserve on demand capacity on an availability zone


## Placement Groups

Define how EC2 are spread out across a region.

- Cluster - consolidate on same server rack
- Spread - across AZs
- Partition - a mix of Spread and Cluster


## Hibernate

Saves RAM state and allows for faster OS boot up.


# Storage

- [[EC2 Instance Store]]
- [[EBS]]
- [[EFS]]


# AMI

Amazon machine image

Create a re-usable customized EC2 instance

Scoped by region


# ASG

Autoscaling groups

Automatically scale number of EC2 instances

### Configuration

- Launch template
- min, max, and initial capacity
- scaling policy
	- target - maintain metric
	- step - scale based on alarm
	- schedule - scheduled actions
	- predictive - use machine learning to automatically scale
- cool down period - no scaling actions during cooldown period
