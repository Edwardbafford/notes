
The HMAC process uses a key that is shared by all servers and the users token to produce a tag.

This tag is appended to the token and returned to the user.

When the user returns the token and tag the the token must be validated with the key to match the tag.This prevents the token from being changed.

The token tags are also not stored in the database so stolen token won't work when submitted because the tag is needed.

In the same way tokens added to the database won't work because the hackers won't know the tag.

![[HMAC.jpg]]
