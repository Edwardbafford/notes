Protocol for implementing Single Sign On and/or managing users through an external system.

Older and should be replaced with [[OpenID Connect]] when possible.


## Terms

- **Subject** - entity to be authenticated
- **SAML Assertion** - XML message containing security information about the subject
- **SAML Profile** - specification defining how to use SAML messages
- **Identity Provider** - a server which issues SAML assertions and authenticates users
- **Service Provider** - delegates authentication to an identity provider
- **Trust Relationship** - Agreement between a service provider and an identity provider that allows the service provider to trust assertions
- **SAML Protocol Binding** - how SAML message elements are mapped to communication protocol. Usually only need to worry about HTTPS.


## Metadata

Serive provider and Identity Provider exchange metadata which contains information such as URL endpoints and digital certificates and establish a Trust Relationship.

Certificates can allow Identity Providers to digitally sign their assertions allowing users to trust the SAML Assertion.


## IdP-Initiated Flow

Login is initiated from corporate login portal which coordinates between an Identity Provider and a Service Proivder. Recommended to use SP-Initiated SSO instead.


## SP-Initiated SSO

1. Subject visits the service provider
2. Service provider redirects the subject's browser to the Identity Provider with a SAML Authentication request
3. Identity Provider authenticates the subject through the browser
4. Identity Provider redirects the subject's browser back to the Service Provider with a SAML Authentication Assertion
5. Service Provider validates the SAML Authentication Assertion and accepts the subject as authenticated


## Configuration
| Element| Description|
| ----------- | ----------- |
| SSO URL| URL where Serive Provider sends authentication requests|
| Certificate| Identity Provider Certificate, used to validate SAML Assertion signatures|
| Protocol Binding| Protocol used by SP and IdP|
| Request Signing| Whether to digitally sign authentication requests and if so define the algorithm|
| Request Encryption| Whether to encrypt authentication requests and if so defines the algorithm|
| ACS URL| URL to send the SALM Assertion response back to|
| Certificate| Serive Provider Certificate, used to validate SAML authentication requests|
| Response Signing| Whether to digitally sign SAML Assertion responses and if so define the algorithm|
| Response Encryption| Whether to encrypt SAML Assertion responses and if so defines the algorithm|


## Authentication Request
| Name| Purpose|
| ----------- | ----------- |
|AssertionConsumerServiceURL| Response URL|
|AuthnRequest| Type of request|
|Destination| URL for IdP. Prevents message forwarding to other endpoints.|
|ForceAuthn| Request to IdP to force subject to authenticate|
|ID| ID for each request, passed back in the response and should be validated by the Serive Provider to prevent [[Cross Site Forgery Request]]|
|Issue Instant| Time request was issued, IdP can reject if this timestamp is to far away|
|Issuer| Service Provider to be checked by the IdP to make sure it's registered|
|NameIDPolicy| SP requests type of identifier to use by the IdP when authenticating the user|
|ProtocolBinding| Underlying transport protocol|
|ProviderName| Name of SP|
|RequestedAuthnContext| Specify requirements for the authentication|
|Signature| Signature information|
|Signature Subject| Specify subject|
|Version| SAML version, should be 2.0|


# Authentication Response

- Response
	- Issuer
	- Status
	- Assertion
		- Issuer
		- Signature
		- Subject
		- Conditions
		- AuthnStatement
		- AttributeStatement
			- Attribute

## Response
| Name| Purpose|
| ----------- | ----------- |
|ID| Unique ID for response|
|InResponseTo| ID sent in the request, used to prevent CSFR|
|IssueInstant| Time response was issued, SPs can reject old responses|
|Destination| ASC URL, SPs should validate this is correct|
|Issuer| IdP who's sending the response|
|Status| Result of authentication request|

## Assertion
| Name| Purpose|
| ----------- | ----------- |
|ID| Unique ID for assertion|
|IssueInstant| Time assertion was issued, SPs can reject old assertions|
|Issuer| IdP who's sending the response|

### Signature
| Name| Purpose|
| ----------- | ----------- |
|SignatureMethod| Signature algorithm used by the IdP|
|Certificate| IdP's certificate for trust relationship|

### Subject
| Name| Purpose|
| ----------- | ----------- |
|NameID| ID of the authenticated user|
|NotOnOrAfter| Validity period of the subject|
|Recipient| ACS URL|
|InResponseTo| ID of the authenticated request|

### Conditions
| Name| Purpose|
| ----------- | ----------- |
|NotBefore| Timestamp should have passed when recieved|
|NotOnOrAfter| Timestamp should not have passed when recieved|
|Audience| Intended repient of the assertion, the SP|

### AuthnStatement

Contains information about the authentication process

### Attribute Statements

Conveys additional user profile attributes about the user.

