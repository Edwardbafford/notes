
SREs apply software engineering for system administrator work to reduce toil and improve development speed and reliability.

**Toil** is work tied to running a production service that is manual, repetitive, and does not add lasting value.

Automating toil makes processes more **reliable**.

Reliability Hierarchy
- [[#Monitoring|Monitoring]] - allows for awareness of issues
- [[#Incident Management|Incident Management]] - how issues are handled
- [[#Release Procedures|Release Procedures]] - to prevent changes from causing issues
- Robust designs - to minimize the impact of incidents



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


## Incident Management

### On-Call

Engineers should be on-call to handle incidents that are detected from [[#Monitoring|monitoring]].

Alerts should notify on-call engineers and be escalated if not acknowledged.

You should have enough engineers to prevent people from being on-call too often.

Effort should be put in to prevent on-call engineers from being overworked.

### Troubleshooting

Effective troubleshooting is key during an incident response to minimize downtime.

When possible minimize downtime over root cause analysis.

Troubleshooting workflow
- Observe behavior
- Hypothesize problem
- Test hypothesis
- Treat successfully tested hypotheses

Systematically moving across a system from component to component is often effective.

Analyzing what has changed recently is a good heuristic for creating hypotheses.

Specialized troubleshooting tools can speed up the process.

### Incident Response

Incidents response should have an outline process with defined roles.

Incident criteria
- Customer outage
- 2nd team is needed
- Production issue is unsolved after an hour

Roles
- Incident commander
	- Assigns responsibilities
	- Hold all positions that haven't been delegated
	- Removes roadblocks
	- Keep a living document of the incident
- Operational Work - only group modifying the system during an incident
- Communication
	- Public face of response team
	- Send out updates to stakeholders

Commander hand-off needs to be done very clearly.

Communication can be down via a war room, chats, and emails.

Practice incident response by intentionally breaking things.

### Postmortem

**Postmortems** are records of an incident with
- impact
- actions taken to mitigate
- root cause
- follow-up actions to prevent further issues

Used to learn from and prevent future similar incidents.

Should be blameless so that incidents aren't covered up.

Should be collaborated on, reviewed, and emailed out once complete.

### Incident Tracking

Track incidents in a system to understand if you need more or less effort towards prevention.

Collect all alerts and map to incidents.


## Release Procedures

Ideally tests and deployments should be bundled together into a single pipeline.

### Testing

Testing is used so that we can be confident that changes don't break things.

Types
- Unit tests - validate independent components
- Integration tests - validate assembled components
- System - validate end-to-end functionality of an entire system
	- Smoke tests - validate simple but critical behavior
	- Performance tests - validate acceptable performance
	- Regression tests - validate that previously identified issues have been fixed

Developing tests has a cost that should be weighed.

Start by building a simple pipeline and begin with the most important tests. Flesh the system out over time.

### Deployments

Teams should be able to push deployments in an easy, reliable, and independent way.

Teams should be able to deploy any version they want in this way.

Deployments should be gated with
- code reviews
- security checks
- lower environment deployments

**Canary deployment** deploys a release incrementally, starting with a small percentage of the system and increases until the new release makes up all of the system. The system is rolled back if errors are detected.






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





