<h2>Status: Development stoopped - it involves a complex query time parser, we are waiting for C# transformations to help with it</h2>

<h3>Template</h3>

The current Google Workspace connector, az function based, relies on 22 different endpoints. The schema is similar with all of them, only the application name at the end of the endpoint URL changes. As the response schema is the same for all endpoints everything is sent to the same table. 

When comparing with the function based connector, we realised the function connector was parsing the logs at the function level. To get to the same log result we had to create a query time parser, also included in this folder. The parser uses compute expensive operators, that are not suited for environments with a lot of logs. 

* GoogleWorkspaceConnector.json - Connector with 22 rules, only allows 1 Google Workspace environment, which I believe suits most customers.

* GoogleWorkspaceConnector1Activity.json - Connector with just 1 rule, ideal for testing.

* GoogleWorkspaceMultipleDomains.json - Connector with 22 rules, it allows adding multiple Google Workspace domains. I could not figure out how to identify the domain name, the interface asks for it just for identification purposes, but I cannot include it in the connector's grid, it just stays blank.

* GoogleWorkspaceConnectorwithCopy.json - it doesn't work. Here we tried to use an ARM propery to make the template easier to read, that would iterate through an array with all the application names, and create a CCP rule for each, instead of us manually having to add 22 CCP rules for each of the endpoint. This arm function doesn't seem to work with CCP templates.

<h3>Documentation</h3>

**Autehtnication:** https://pnatraj.medium.com/google-cloud-api-with-postman-f4cf070e665f

**Endpoint:** https://developers.google.com/admin-sdk/reports/reference/rest/v1/activities/list

<h3>Testing considerations</h3>

It took us awhile to understand that you need more than a GCP trial. You need a Google workspace trial. 
You will need to own a domain to get access to a google workspace trial. Then, you use the GCP environment to [create the Oauth application](https://pnatraj.medium.com/google-cloud-api-with-postman-f4cf070e665f).
Don't forget to [enable API logging](https://support.google.com/a/answer/7281227?visit_id=638463106488553876-3203949728&rd=1)
