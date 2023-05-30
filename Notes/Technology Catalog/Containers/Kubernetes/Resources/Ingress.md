Acts as a gateway into the K8s cluster and enables traffic routing based on URL path and hostname.

## Format

Under spec
- `rules`
	- `host` - only apply rule to a host
	- `http`
		- `paths`
			- `path` - URL path
				- `backend`
					- `serviceName` - service name to route to
					- `servicePort` - port of service