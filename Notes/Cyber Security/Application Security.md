

## Incoming Requests

* Use an [[API Gateway]] as the entry point to the system to enforce security features and minimize attack surface
	* Enforce rate limiting to prevent [[Denial of Service|DoS]] attacks
* Enforce [[Authentication|authentication]]
	* Don't deny until after audit log
	* Deny with 401
* Create [[Audit Log|audit logs]]
* Enforce [[Authorization|authorization]]
	* Deny with 403

![[API Security.jpg]]


## General

* Encrypt data while traveling across the network
	* Usually using [[HTTPS]]
* Encrypt data at rest
* Create a [[Zero Trust Network|zero trust network]] where even internal service requests must be authenticated and authorized
* Endpoints should not expose any revealing error messages
* Limit [[CORS]]
* Implement [[Container Security|container security]] if applicable
* Incorporate security into the [[Devops]] process
	* Testing
	* Code Reviews
	* Static code analyzers
	* Scan for vulnerabilities
* Proper [[Service-to-Service|service-to-service]] authentication and authorization
* Proper [[Secret Management|secret management]]