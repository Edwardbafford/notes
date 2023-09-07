
SREs apply software engineering for system administrator work to reduce toil and improve development speed and reliability.

**Toil** is work tied to running a production service that is manual, repetitive, and does not add lasting value.

Automating toil makes processes more **reliable**.

Reliability Hierarchy
- [[#Monitoring|Monitoring]] - allows for awareness of issues
- Incident Response - how issues are handled
- Tracking incidents - allows us to learn from incidents
- Testing and Release procedures - to proactively prevent incidents
- Robust designs - to proactively prevent incidents



Change management
1. Automated progressive rollouts
2. Automated detection
3. Automated rollbacks

Scalability
1. Load prediction
2. Load testing based off of predictions



## Monitoring

Collection real time data from a system.

**White box monitoring** measures system internals.

**Black box monitoring** measures externally visible behavior.

Monitoring systems should be kept as simple and reliable as possible so that we don't need to monitor our monitoring system!

Monitoring can be used for
- System analysis
- Detect issues and alert developers

Alerts are triggered by metrics.

False positive alerts need to be minimized.

### Metrics
- Latency
- Traffic
- Errors
- Resources
	- Storage
	- CPU
	- Memory

Metric data should be collected across time for all systems and aggregated into potential alerts.

### Service Level Objectives

**Service level indicators** are metrics that are important to a service in some way.

SLIs work off of your monitoring system.

**Service level objectives** are target values/ranges for service level indicators.

**Service level agreements** are contracts constructed around SLOs.

SLOs should be based around what the customers care most about!

SLOs should be used as a resource for guiding development.

Alerts should be shaped to SLOs.

Different SLOs have different trade-offs and can be adjusted over time.


## Availability

Increasing availability increases costs and decreases development speed. So we need to decide how much effort to put into availability.

Good availability metric is **request success rate** 

What availability is acceptable? Consider the trade-offs

Availability influences
- Fault tolerance
- Testing
- Push frequency
- Deployment methodology

Create a specific quarterly availability goal. If the goal is being met feel free to increase development if not slow down development and focus on availability. If availability is too hard to hit, decrease the metric.


## Release Management

Teams should be able to push deployments in an easy, reliable, and independent way.

Teams should be able to deploy any version they want in this way.

Deployments should be gated with
- code reviews
- security checks
- lower environment deployments


