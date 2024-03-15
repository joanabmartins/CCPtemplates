I created this template, when I was just starting to study CCP. 

It still uses the old template format with tempalte specs instead of being content template.

Azure activity logs are an easy source to get access to, so it was a nice way to start learning CCP without having to subscribe to trials.

We just need to register a new application in Entra ID, create a new secret, and give it RBAC access to get the activity logs at the subscription level.

When deploying the template you need the put the entire token endpoint and activity logs endpoint: 

https://login.microsoftonline.com/<tenant ID\>/oauth2/v2.0/token

https://management.azure.com/subscriptions/<subID\>/providers/Microsoft.Insights/eventtypes/management/values

I didn't really explore pagination for this API.
