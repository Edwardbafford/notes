Elastic Load Balancer

Managed load balancer

Use [[Security Group]] for access

**Health Checks:** check instance health to know which ones are available. Define request and check for 200 response.

**Sticky Sessions:** ELB gives a cookie which will route to the same backend instance for every request with that cookie.

**Target Group:** Define a set of instances to provide load balancing

**Cross Zone Load Balancing:** Splits requests evenly across all instances, even between AZs. Without this enabled requests are balanced with AZs only.

**Connection Draining:** Wait to close requests on de-activated instances.


## Classic Load Balancer

Legacy load balancer

TCP and HTTP/S

#### Features
- stick session
- connection draining


## Application Load Balancer

HTTP and WebSockets

X-forward-... for determining client information

#### Features
- target groups - based off of path, hostname, query strings, and/or headers
- sticky sessions
- connection draining
- cross zone load balancing
- multiple domain names
- health checks


## Network Load Balancer

TCP and UDP

Directly forwards request from client

Extreme performance

#### Features
- target groups - based off of port, hostname, and/or protocol
- connection draining
- cross zone load balancing
- multiple domain names
- health checks


## Gateway Load Balancer

IP Level

Used to route traffic through 3rd party security appliances