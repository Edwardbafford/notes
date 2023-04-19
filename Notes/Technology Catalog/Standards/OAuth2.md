OAuth is a protocol used by Authorization Servers to give a client limited API access on behalf of a user without having to use their credentials.

OAuth2 is intended for [[Authorization|authorization]] not [[Authentication|authentication]]. If you're looking for a similar framework tailed to authentication use [[OpenID Connect]]!


# Roles

**Resource Server** - a service with protected resources

**Resource Owner** - user that owns the protected resources

**Client** - an application trying to access the protected resources on behalf of the resource owner

**Authorization Server** - a service trusted by the resource server used to authenticate the resource owner and grant access to the client


# Scopes

Scopes are defined within the AS and given in the access token. 

Each scope is supposed to represent certain permissions or [[Authorization|authorization]] level which should be enforced on the API side.


# Clients

Client must be registered with the AS and gets a unique client ID.

Scopes are defined per client.

**Public Clients** are applications that cannot securely store credentials such as browsers or mobile apps.

**Confidential Clients** are applications which can use their own credentials to identify themselves.


# Authorization Flow

1. Client requests API access on behalf of a client
2. Resource owner grants access for the client to access the API
3. AS returns an access token
4. Access token is used by client when interacting with API
5. API validates token with AS

![[OAuth2.jpg]]


# Tokens

**Authorization Code** - An intermediary token used to exchange with an access token one time.

**Access Token** - A token used by the client to access the resource server.

**Refresh Token** - An optional token that can be used to request a new access token.


# Grants

Grants are how the client gets an access token from the authorization server.

* [[Client Credentials Grant]]
* [[Authorization Code Grant]]


# Refresh Token

Refresh token can be returned with access token and can be used by the client to get new access tokens.

Authorization servers must implement either **refresh token rotation** or **sender-constrained tokens**.

**Refresh token rotation** returns a new refresh token for each access token. If a refresh token is used twice the authorization server will alert it's users.

**Sender-constrained tokens** use cryptographic signatures to bind the refresh token to the client.


# Validate Token

The API needs to validate the token passed in from the client.

## Introspection

1. Register client with AS and get credentials in return
2. Submit token to AS introspection endpoint along with credentials

Result can be cached so that validation requests aren't needed for every request but you could accept an invalidated token

## Signed Tokens

1. AS signs token with private key
2. [[JWT]] can be validated with AS public key held by API

No need for validation calls.

How do you revoke?


# Token Revocation

Submit access token and credentials to the revoke endpoint when they are no longer needed.

Only the client can use the revoke endpoint.