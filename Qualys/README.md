<h2>Qualys Connector Status: Testing with customer, it uses a complex parser</h2>

Relatively straighforward connector to deveop. The main issue we were facing is with the parser. 
The existing connector was relying on the Azure Function to parse each detection from each host in a separate log. 
When we use CCP we have one log per host, with all the detections. To split them we cannot use an ingestion time trasnforamtion (mv-expand is not supported). 
We need to use a query time function, though mv-expand is not recommended on them.

<h3>Template</h3>

* Connector template - I believe this template is pretty ready for publishment.

* Parser - The parser was built to generate exactly the same fields as the old connector. However, all the out of the box content used with the function based connector directly query the old table.
We need to include the old table in this parser (with union), and update all the out of the box content to query the function parser, instead of the old table directly.

<h3>Documentation</h3>

https://cdn2.qualys.com/docs/qualys-api-vmpc-user-guide.pdf

        API Endpoint: /api/2.0/fo/asset/host/vm/detection/

<h3>Testing Considerations</h3>

There is a free trial available, relatively easy to generate logs and test this connector.
