
# API Key

Long last key passed in with requests.

Needs a database to be verified and linked to permissions.


# JWT Token

[[JWT]] or other self-contained token contains all data needed - scope and claims.

Encrypted with client private key and decrypted with server's public key.

Use audience field to limit where token could have been sent from.

Revoke by rotating private/public key pair.


# Authorization Server

Many AS have simpler "login" methods for service clients.

### OAuth2

For [[OAuth2]] servers use the **Client Credentials Grant** or the **JWT Bearer Grant**. 

Use a **service account** as the user the service is acting on behalf of.


# Mutual TLS

Server provides cert then requests client cert.

Server verifies client cert and parses it to get user identity.

Can be combined with other approaches.


# Phantom Token

One service validates a token from a user then creates a new short lived self-contained token (such as [[JWT]]) which it passes on to other services while completing a request.

[[OAuth2]] allows for this with a token exchange endpoint.