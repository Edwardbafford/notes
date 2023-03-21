Standard **self-contained** token format.

Contains three parts separated by a period

-   Header - contains algorithm details and should always be verified by services processing the token
-   Claims
-   [[HMAC]] tag

Has standard claims

-   subject - the user
-   expire - when the token expires
-   audience - who the token is for (which API/s)

**JWE** provides an encryption standard method for JWT tokens.