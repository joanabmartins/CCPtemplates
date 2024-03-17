<h2>Status: Development stoopped - it involves a complex query time parser, we are waiting for C# transformations to help with it</h2>

<h3>Template</h3>

The current Google Workspace connector, function based, relies on 22 different endpoints. The schema is similar with all of them only the application name at the end of the endpoint URL changes. 
So, we tried to use an arm propery to make the template easier to read, that would iterate through an array with all the application names, and create a CCP rule for each. However, that template doesn't work. 
We ended up manually adding 22 rules for the Google Workspace connector.

As the response schema is the same for all endpoints everything is sent to the same table. 

When comparing with the function based connector, we realised the function connector was parsing the logs at the function level. To get to the same log result we had to create a query time parser. You can also check it here. 
The parser uses compute expensive operators, that are not suited for environments with a lot of logs. 

<h3>Documentation</h3>

**Autehtnication:** https://pnatraj.medium.com/google-cloud-api-with-postman-f4cf070e665f

**Endpoint:** https://developers.google.com/admin-sdk/reports/reference/rest/v1/activities/list

<h3>Testing considerations</h3>

It took as awhile to understand that you need more than a GCP trial. You need a Google workspace trial. 
You will need to own a domain to get access to a google workspace trial. Then, you connect your google workspace to you GCP environment to create the Oauth application.
