
Client needs to be a **Confidential Client**

1. The client sends an authorization request with credentials to the authorization server
2. Authroization server responds with an access token

Client needs to be registered with the authorization server.

No need for refresh tokens!


## Authorization Request

Encoded application credentials are passed into the request, usually through a header.

Other request parameters
| Parameter| Description|
| ----------- | ----------- |
| grant_type| client_credentials|
| score| The scope being requested access for|
| resource| Also known as "audience", defines the **Resource Server** the access token is needed for|


