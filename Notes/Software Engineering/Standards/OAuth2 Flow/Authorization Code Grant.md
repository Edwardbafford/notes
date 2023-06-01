
1. Resource owner access the client
2. Client redirects browser to the authorization server's authorize endpoint with an authorization request
3. The authorization server prompts the user to authenticate
4. The resource owner authenticates and consents to authorizing the client
5. Authorization server redirect's the users browser back to the client's callback URL with an **authorization code**
6. Client calls the authorization server's token endpoint with the authorization code
7. Authorization server responds with an access token

## PKCE

PKCE (Pixie) adds an extra layer of security to mitigate issues if the authorization code is stolen before it is exchanged for the access token

During the grant process the client creates a **code verifier** value and a **code challenge** value.

**Code Verifier** is a random value

**Code Challenge** is a hashed version of the code verifier (usually S256)

On the authorize request the client passes in the code challenge value to the authorization server.

On the token request the client passes in the code verifier value to the authorization server.

The authorization server must verify that the code verifier hashes into the code challenge before returning the access token.

Because only the client knows what the proper code verifier is it will be the only one to get the access token even if the authorization code was stolen.


# Authorization Call

## Request
| Parameter| Description|
| ----------- | ----------- |
| response_type| "code" indicating the authorization code grant|
| client_id| ID of the registered client|
| state| unique string sent for each call, used to mitigate CSFR attacks|
| scope| The scope being requested access for|
| redirect_uri| call back URL to send the response to, but it must match a registered URI|
| resource| Also known as "audience", defines the **Resource Server** the access token is needed for|
| code_challenge| PCKE code challenge value|
| code_challenge_method| Hash algorithm for the PKCE code challenge|

## Response
| Parameter| Description|
| ----------- | ----------- |
| code| Authorization code|
| state| state value sent to the authorization server|

Client must validate that the state token matches one of the ones sent to the authorization server. This way is a user was tricked into sending an authorization request from a different source the client will not accept the authorization.


# Token Call

## Request
| Parameter| Description|
| ----------- | ----------- |
| grant_type| "authorization_code"|
| code| Authorization code value|
| client_id| ID of the registered client|
| code_verifier| PKCE code verifier value|
| redirect_uri| call back URL to send the response to, but it must match a registered URI|


## Response
| Parameter| Description|
| ----------- | ----------- |
| access_token| The access token to access the resource server|
| token_type| Type of token issued, for example "Bearer"|
| expires_in| When access token expires|
| refresh_token| Refresh token for getting a new access token|


