<h2>Status: Development stopped</h2>

We were successful in getting logs from reaching directly to the google iam API through CCP, but ended up stopping the development because we discovered there was already a CCP solution published in Sentinel to get these logs. 
This solution instead of using Oauth, uses pub/sub and aims to get any gcp audit log, not only IAM. PG informed us customers prefer to do it like that. We stopped developing this solution further.

<h3>Template</h3>
The templte works fine. We didn't explore the table schema too much. 

<h3>Documentation</h3>

**Authentication:** https://pnatraj.medium.com/google-cloud-api-with-postman-f4cf070e665f

**Log Endpoint:** https://cloud.google.com/iam/docs/audit-logging#api
