<h2>Snowflake status: Under development - needs troubleshooting with PG</h2>

Current Issue:
Snowflake API uses Oauth code authentication.When trying ot authorize we get the error invalid consent. Thrugh research it seems like it has something to do with scopes, and indeed if when testing through Postman,
we remove scope we get the same error. However, we are adding scope, in Postman it work, I've reviewed the headers and everything through the Dev Tools, the requests that CCP does and Postman does seem identical. 
I don't understand what could be the issue.

https://community.snowflake.com/s/article/Invalid-Consent-Request-while-using-OAuth-for-Custom-Clients

