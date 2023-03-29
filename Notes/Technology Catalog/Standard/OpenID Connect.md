[[OAuth2]] is designed mainly for allowing 3rd parties to access information on behalf of a user.

On the other hand, OpenID Connect extends OAuth with the intention of authentication and SSO functionality.

1.  Client calls an authorization endpoint to get an authorization code
2.  Then the client exchanges the code for an access token
3.  Client can then use the access token to call the UserInfo endpoint to retrieve the identity claims for the user

With OpenID Connect the AS acts like the API with its UserInfo endpoint

An ID Token can be returned with the auth code or the access token depending on the AS. An ID token is used for authentication not authorization.