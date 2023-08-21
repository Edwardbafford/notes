
SREs apply software engineering for system administrator work to reduce toil and improve development speed and reliability.

**Toil** is work tied to running a production service that is manual, repetitive, and does not add lasting value.



Metrics
- Availability
- Scalability
- Latency
- Cost
- Change management
- Monitoring

Monitoring
- Alerts - notifications signaling human intervention is needed
- Logging - records which can be used for analysis

Emergency Response - mean time to repair

Change management
1. Automated progressive rollouts
2. Automated detection
3. Automated rollbacks

Scalability
1. Load prediction
2. Load testing based off of predictions


## Service Level Objectives

**Service level indicators** are metrics that are important to a service in some way.

**Service level objectives** are target values/ranges for service level indicators.

**Service level agreements** are contracts constructed around SLOs.

SLOs should be based around what the customers care most about!

SLOs should be used as a resource for guiding development.

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



