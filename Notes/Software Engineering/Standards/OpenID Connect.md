
Protocol layer on top of [[OAuth2]] designed to allow authorization servers to authenticate users on behalf of an application.

In this use case there is only one application.

## Roles

**End User** - subject to be authenticated

**OpenID Provider (OP)** - [[OAuth2]] authorization server that implements OIDC

**Relying Party (RP)** - Client which delegates user authentication to an OpenID Provider


## Tokens

Authorization code, access token, and refresh token. Reference [[OAuth2]] for descriptions.

**ID Token** - [[JWT]] token which contains claims about the authenticated user. Token is signed in accordance with JWS (JSON Web Signature) specification. Optionally encrypt the token with JWE (JSON Web Encryption) specification.

Common claims included with the ID Token

| Claim| Description|
| ----------- | ----------- |
| iss| Issuer of token, identifier for the OpenID Provider|
| sub| ID of the authenticated user|
| aud| ID of the relying party|
| exp| Expiration time for the ID token|
| iat| Time the token was issued|
| auth_time| Time the user was authenticated|
| nonce| String used to prevent ID token replay exploits|
| amr| Authentication method used by the OP|


## Endpoints

Authorize and token endpoints as described in [[OAuth2]] protocol.

**UserInfo** - returns claims about an authenticated user but requires an access token.


## Flows

- [[OIDC Authorization Code Flow|Authorization Code Flow]]
- Implicit Flow
- Hybrid Flow

Authorization code flow returns ID Token with the Access Token in the backend to backend call.

Implicit Flow does not return an Access Token at all and returns the ID Token through the browser in place of the authorization code.

Hybrid Flow returns the ID Token through the browser along with an authorization code. The authorization code can be used to get an access code if necessary.

Because the ID Token is not as confidential as an Access Token it can be returned through a browser redirect without much risk. This is what allows for the implicit and hybrid flows.