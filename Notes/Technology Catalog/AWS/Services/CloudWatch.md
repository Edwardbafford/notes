
## Metrics

**Metrics** are variables to monitor

**Default metrics** provided for every service

Metrics can be scoped within **namespaces**

**Dimensions** are attributes of a metric. Metrics can have up to 10 dimensions.

Users can create **custom metrics**.

Combine metrics into **dashboards**

Stream metrics into other systems using [[Kinesis Firehouse]]


## Logs

A **Log Group** is a container for log streams

A **Log Stream** is an instance of log collection
- Expiration Policy
- Can come from a **Custom Agent** or an **AWS Service**

A **Unified Agent** is a tool for collecting logs and sending it to CloudWatch.

Use logs and a filter to create metrics and trigger alarms

**Log Insights** can be used to create queries

Logs can be exported

Subscriptions can be created for logs


## Alarms

Trigger notifications based on metrics

States
- Ok
- Insufficient Data
- Alarm

**Period** is the length of time of which a metric is evaluated

**Composite Alarms** aggregate multiple alarms into a single alarm

Test alarms using CLI to set alarm state


