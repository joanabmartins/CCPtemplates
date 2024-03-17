<h2>Status: CCP NOT SUPPORTED</h2>

We have studied the alibaba environment and arrived to the conclusion that it was not supported because the Simple Log Service API has its own way of authenticating. It doesn't support Oauth, Baisc or API key.
**We couldn't make any call through Postman**. We checked with Ali Cloud support and they confirmed it. 
The authentication is based on signatures, and you need to use their SDKs to generate these signatures.

https://www.alibabacloud.com/help/en/sls/developer-reference/request-signatures

I believe there is a way around this which is to use an ali cloud service called Event Bridge. 
We can send the logs from the Simple Log Service to Event Bridge, and collect them from Event Bridge through an API call. **Event Bridge API supports Oauth**.

https://www.alibabacloud.com/help/en/eventbridge/user-guide/log-service

https://www.alibabacloud.com/help/en/eventbridge/user-guide/manage-api-destinations

Our customer didn't want to explore the Event Bridge option as it involved extra work and costs in Ali Cloud.  

Ali Cloud supports a **free trial**, but I was never able to actually produce any logs and send them to the Simple Log Service, let alone test the Event Bridge option.
