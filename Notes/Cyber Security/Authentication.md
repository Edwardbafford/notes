A number of interrelated approaches exist


# **Mutual TLS**

Runs on top of standard [[HTTPS]] protocol where after the client verifies the servers identity, the server verifies the clients identity using a signed public certificate.

# Username and Password

User is authenticated by providing their password.

Passwords when created should be salted and hashed then stored. Incoming authentication attempts should be salted and hashed then compared. This is so if the hashed passwords are stolen they cannot be known.

Password verification should be forced to execute slowly in order to prevent brute force attacks.

Passwords verification to should fail or succeed at the same speed to avoid [[Timing Attack|timing attacks]].

## Implementation

* [[Basic Authentication]]



# Tokens

Tokens can be temporarily used in place of a password to avoid sending the password over the network every time and to avoid the slow validation process necessary for passwords.

## Basic Flow

1.  Login with username and password authentication
2.  Once authenticated create a token and give it to the user
3.  Validate this token as authentication on each request
4.  Invalidate tokens on logout

## Implementation

Token storage should be simple and fast such as a cache or NoSQL database.

Tokens should be generated in a way that is cryptographically secure.

Delete consistency is important for invalidating tokens.

Expired or invalidated tokens need to be removed from the database.

Using [[HMAC]] encryption to ensure the following properties:

-   tokens cannot be changed
-   tokens stolen from DB cannot be used
-   tokens added to the DB won't work
-   rejects tokens in constant time

Store tokens in browser localStorage.

## **Self Contained Tokens**

Token itself contains a set of claims (or information) about the user.

Servers can get data from the token instead of a database.

This helps with scaling and distributed applications.

[HMAC](#HMAC) prevents claims from being altered within the token.

The claims within the tokens should usually be encrypted so only the servers can understand them.

To implement token invalidation at least one token claim needs to exist within a database where it can be verified and deleted.

## **Standards**

- [[Cookies]]
- [[JWT]]


# Authorization Servers

Dedicated servers used for authenticating and authorizing users on behalf of other APIs.

Outsources most of the work.

## **Standards**

- [[OAuth2]]
- [[OpenID Connect]]
- [[SAML]]

## **SSO**

Use AS to centralize authentication across multiple applications

Clients authenticate with Authorization Server and get returned a cookie.

Browser uses cookie automatically get authenticated to the Authorization Server when accessing any APIs linked with the AS.

In this way, signing into the AS for one API will allow you to automatically access all API linked with the AS. You only needed a single sign on!