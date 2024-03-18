<h2>Trend Micro Cloud App Security Status: Working for one customer, issue when trying to connect 48 endpoints</h2>

Trend Micro security events API has a different endpoint of each service (12) and each event (4) (exchange/securityrisk, exchange/virtualanalyzer, exchange/ransomware, exchange/dlp, sharepoint/securityrisk, ...). 
My customer just wanted to connect to 4 of these services, with 4 events (16 endpoints). We developed the template and it works fine, better than the one based on azure function. 
With the azure function connector they were getting errors and we were able to observe that the CCP connector is ingesting more logs than the one based on az function.

When adding 48 endpoints (instead of the 16 that we created for the customers), **we can't connect all of them**. The Trend Micro API has this limitations:

    Error Code 429: The user has made more than 20 requests over the past 1 minute and has been throttled. 
    The user can start new requests in the next minute from the first request.

Solution suggestions:

* Allow customer to select which endpoints they want to connect to. Trust they won't want to connect to more that 20 - this is not possible today but it is on the roadmap

* Split the connector into 2-3 different ones (each one with 15-20 rules), and make sure we connect them at different times, to avoid querying the API all at once.

* Develop the possibility to randomize rule start time within a range of query window for example (instead of the default 1 second.

* Contact Trens Micro to understand if there is a possibility to increase rate time


<h3>Template</h3>

As stated above the template cannot connect the 48 endpoints. It does succesfully connect to a few. The DCR transforms the logs to use the same field names as the function based connector. 
Once the throttling issue gets solved, we still need to change the existing parser to include this new table. After that if we don't care for ASIM I believe this connector is ready for publishing.

<h3>Documentation</h3>

https://docs.trendmicro.com/en-us/documentation/article/cloud-app-security-integration-api-online-help-get-security-logs

<h3>Testing Considerations</h3>

There is a free trial available, it is easy to use.
