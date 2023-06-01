
Similar to [[OAuth2]] [[Authorization Code Grant]]

Also optionally uses PKCE

## Steps

1. End user accesses the relying party
2. End user's browser is redirected to the OpenID provider authorize endpoint
3. End user authorizes with the OpenID provider
4. The browser is redirected back to the application with the authorization code
5. The relying party sends a token request to the OpenID provider with the authorization code
6. OpenID provider responds with an ID Token, access token, and optionally a refresh token
7. The relying party can use the access token on the UserInfo endpoint


# Authorization

## Request
| Parameter| Description|
| ----------- | ----------- |
| response_type| "code" indicating the OIDC authorization code flow|
| response_mode| How the authorization response returns it's parameters|
| client_id| ID of the registered client|
| state| unique string sent for each call, used to mitigate CSFR attacks, see [[Authorization Code Grant]] for further details|
| nonce| value passed to OpenID provider to help protect against token replay attacks|
| scope| claims requested about the authenticated user|
| redirect_uri| call back URL to send the response to, but it must match a registered URI|
| resource| Also known as "audience", defines the **Resource Server** the access token is needed for|
| code_challenge| PCKE code challenge value|
| code_challenge_method| Hash algorithm for the PKCE code challenge|

The response_mode parameter can indicate to the OpenID provider how it will return the parameters. Either in query strings in a fragment appended to the redirect URI.

The nonce value is tied to a session created between the end user and relying party.  The relying party must validate that the nonce token in the ID Token matches the nonce token linked to the users session. This prevents that same ID Token from being re-used for new authentication attempts.

## Response
| Parameter| Description|
| ----------- | ----------- |
| code| Authorization code|
| state| state value sent to the authorization server|

Validate state!


# Token

## Request
| Parameter| Description|
| ----------- | ----------- |
| grant_type| "authorization_code"|
| code| Authorization code value|
| code_verifier| PKCE code verifier value|
| redirect_uri| call back URL to send the response to, but it must match a registered URI|

## Response

Response is in JSON format
| Parameter| Description|
| ----------- | ----------- |
| id_token| ID Token with claims|
| access_token| The access token to access the UserInfor endpoint|
| token_type| Type of token issued, for example "Bearer"|
| expires_in| When access token expires|
| refresh_token| Refresh token for getting a new access token|

Validate the ID Token with JWS and JWE or use the access token to get claims from UserInfo endpoint.

Validate the nonce value to prevent ID Token re-use.