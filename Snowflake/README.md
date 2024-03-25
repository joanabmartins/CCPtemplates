<h2>Snowflake status: Under development - needs troubleshooting with PG</h2>

Current Issue:
Snowflake API uses Oauth code authentication. When trying ot authorize we get the error invalid consent. Through research it seems like it has something to do with scopes, and indeed when testing through Postman, if
we remove scope we get the same error. However, we are adding scope in the CCP template so we don't understand why it doesn't work, in Postman it does. I've reviewed the headers and everything through the Dev Tools, the requests that CCP does and Postman does seem identical. 
I don't understand what could be the issue.

https://community.snowflake.com/s/article/Invalid-Consent-Request-while-using-OAuth-for-Custom-Clients

There also seems to be a small bug related to inputing the authorization endpoint through the connector UI. If we don't call the authorization endpoint parameter exactly like this: "authorizationEndpoint": "[[parameters('authorizationEndpoint')]" it doesn't work. If we name the parameter authorizationEndpoint2 for example, it doesn't work. If we try to concat it like this: "authorizationEndpoint": "[[concat('https://',parameters('snowflakeAccountURL'),variables('authorizationEndpoint'))]" , which would be ideal, it doesn't work. I've shared this with Michael, it is not a major thing.

