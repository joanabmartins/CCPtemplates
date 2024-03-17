<h2>Status: Not supported</h2>

We based our attempt on what the Az function connector was doing. We got access to an API that gives us the path to hourly event log files, then we need to reach out to this files in CSV to get the logs. 
Nested APIs are not yet supported in CCP.

**API Endpoint Documentantion:** https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/event_log_file_hourly_overview.htm

**Authentication:** Follow this tutorial to create oauth app https://blogs.perficient.com/2023/01/19/how-to-connect-to-salesforce-with-postman/

**First endpoint:** Get https://< salesforce domain >.develop.my.salesforce.com/services/data/v58.0/query?q=SELECT+Id+,+EventType+,+Interval+,+LogDate+,+LogFile+,+LogFileLength+FROM+EventLogFile+WHERE+Interval+=+'Hourly'

Response - File path

**Second Endpoint:** https://< salesforce domain >.develop.my.salesforce.com/services/data/v58.0/sobjects/EventLogFile/< file >/LogFile

<h3>Testing considerations</h3>
Don't forget to enable auditing: go to event manager and enable streaming.


