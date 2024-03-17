<h2>Status: Not supported</h2>

We based our attempt on what the Az function connector was doing. We got access to an API that gives us the path to hourly event log files, then we need to reach out to this files in CSV to get the logs. 
Nested APIs are not yet supported in CCP.

**API Endpoint Documentantions:** https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/event_log_file_hourly_overview.htm

**Authentication:** Follow this tutorial to create oauth app https://blogs.perficient.com/2023/01/19/how-to-connect-to-salesforce-with-postman/

**First endpoints:** Get https://sentinel-dev-ed.develop.my.salesforce.com/services/data/v58.0/query?q=SELECT+Id+,+EventType+,+Interval+,+LogDate+,+LogFile+,+LogFileLength+FROM+EventLogFile+WHERE+Interval+=+'Hourly'

Response - Path with files

**Second Endpoint:** *I need to complete this README file*


