A token implementation used for authentication.

Highly integrated with Browsers which makes it easy to use but limited in flexibility.

Creating a token is also commonly referred to as creating a **session**.

Server returns "Set Cookie" header, which the browser then attaches to each request in the "Cookie" header.

Cookies are associated with a domain and not sent on requests to other domains.

Server can specify certain cookie attributes in the set cookie response which should be as restrictive as possible.

Cookies are susceptible to [[Cross Site Forgery Request|CSRF]] attacks considering the browser automatically attaches them with each request.
