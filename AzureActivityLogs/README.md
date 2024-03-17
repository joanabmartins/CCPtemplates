<h2>Status: CREATED JUST FOR FUN</h2>

I created this template, when I was just starting to study CCP. 

Azure activity logs are an easy source to get access to, so it was a nice way to start learning CCP without having to subscribe to trials.

<h3>Template</h3>

This template still uses the old template format with tempalte specs instead of content template.

For **authentication** you  just need to register a new application in Entra ID, create a new secret, and give it RBAC access to get the activity logs at the subscription level.

When deploying the template you need the put the entire token endpoint and activity logs endpoint: 

https://login.microsoftonline.com/<tenant ID\>/oauth2/v2.0/token

https://management.azure.com/subscriptions/<subID\>/providers/Microsoft.Insights/eventtypes/management/values

I didn't really explore pagination for this API.

<h3>Documentation</h3>

https://learn.microsoft.com/en-us/rest/api/monitor/activity-logs/list?view=rest-monitor-2015-04-01&tabs=HTTP
