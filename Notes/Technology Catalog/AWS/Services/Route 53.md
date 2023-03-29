
[[DNS]] and [[Domain Registrar]]

**Hosted Zone** is a container for records. Can be public or private.


## Records

- Domain name
- Record Type
	- A - maps to IP v4
	- AAAA - maps to IP v6
	- CNAME - maps to hostname
	- NS - maps to another DNS
	- Alias - maps to AWS hostname
- Value
- Routing Policy
	- Simple - returns record value at random if more than one
	- Multi-value - same as simple but works with health checks
	- Weighted - returns record value based on assigned weights
	- Latency - return value based on minimizing latency
	- Failover - monitor value with health check and failover if necessary to secondary value
	- Geolocation - return value based on location of request
	- Geoproximity - return value based on location of request and value biases
- Time to live - how long record is valid for needing to be re-checked


## Health Checks

- Public Endpoint - AWS checkers send requests to public endpoints
- Calculate Health Checks - Aggregate other health checks
- [[CloudWatch]] Alarms - Works for private records