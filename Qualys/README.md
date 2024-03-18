<h2>Qualys Connector Status: Testing with customer, it uses a complex parser</h2>

Two things came up with this connector:

* Qualys API have some strict [rate limits](https://cdn2.qualys.com/docs/qualys-api-limits.pdf). If the response takes too long, we may face timeout, which will prompt to call the API again, and face those limits. We had to increase the timeout window to make it work for the customers, as during scanning time the API was taking more than 2 minutes to respond.

* Parser is a bit complex. The existing connector was relying on the Azure Function to parse each detection from each host in a separate log. 
When we use CCP we have one log per host, with all the detections. To split them we cannot use an ingestion time trasnforamtion (mv-expand is not supported). 
We need to use a query time function, though mv-expand is not recommended to use on parsers.

<h3>Template</h3>

* Connector template - I believe this template is pretty ready for publishment.

* Parser - The parser was built to generate exactly the same fields as the old connector. However, all the out of the box content used with the function based connector directly query the old table.
We need to include the old table in this parser (with union), and update all the out of the box content to query the function parser, instead of the old table directly.

<h3>Documentation</h3>

https://cdn2.qualys.com/docs/qualys-api-vmpc-user-guide.pdf

        API Endpoint: /api/2.0/fo/asset/host/vm/detection/

<h3>Testing Considerations</h3>

There is a free trial available. In the first trial I got I was able to easily connect and generate logs. However when I used another email to get access to a new trial, I discovered that trial accounts aren't supposed to have access to the Qualys API. I don't understand how I was able to get access to the API with my first trial.
