A user is tricked into executing an unwanted action. Actions are within the intended scope of the application but done without the users intention.

Usually this involves specialized links or fake portals which users click/use which automatically executes the unwanted action.

# **Prevention**

GET requests should not change the state of the application since GET requests can be easily forged and accidentally clicked.

Have the application check the origin of the requests. If they do not come from a trusted source they can be rejected.

Use CSFR tokens. A dynamically generated token is created and passed to the user. When submitting a POST request the token must also be submitted proving they came from your website.

![[csrf-token.png]]