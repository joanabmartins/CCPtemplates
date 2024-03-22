<h2>Oracle Fusion Status: It is working for a customer</h2>

We created this connector when Sergio Vallejo (CSA) told us about his customer's need. 

The customer showed us how he was doing the API calls through postman and we translated that to CCP. 

We didn't do anything to normalize the logs. The CCP UI definition may also need extra care, with better api access instructions, etc. 

<h3>Documentations:</h3> 

[Post Audit Report](https://docs.oracle.com/en/cloud/saas/applications-common/24a/farca/op-fscmrestapi-fndauditrestservice-audittrail-getaudithistory-post.html)

[Get Sign-ins and sign-outs](https://docs.oracle.com/en/cloud/saas/applications-common/24a/farca/op-https-servername-oam-services-rest-access-api-v1-audit-events-get.html)

"Fusion Security Using Sign In - Sign Out Audit REST API.pdf" - added to this github directory

<h3>Pagination</h3>

The customer ended up trusting on utilizing no pagination, but we did do some tests:

* Even though the documentation says it may support offset pagination, our tests revealed it doesn't. 

* The post command to receive audit logs support Count Based Paging. The parameters are straight forward pageNumber and pageSize. 
We were able to test it in postman, however we found an issue with Scuba support.
I believe it is fixed now, so it should be working fine, but as I haven't tested in the customer environment, I didn't include paging to this API in the template.

* The Get Sign-in paging is more complexed. Even though in the online docs it says it works like the previous endpoint, with Postman we tested and realized it actually doesn't. 
The page number is included directly in the API url, not as a parameter. As the customer was fine with not using pagination for this, we didn't explore this further. 
This type of paging is documented in the PDF that is added to this folder ("Fusion Security Using Sign In - Sign Out Audit REST API.pdf" page 3).

<h3>Testing Considerations</h3>
It doesn't seem to be possible to have a trial for Oracle Fusion cloud applications: https://docs.oracle.com/en/cloud/get-started/subscriptions-cloud/csgsg/order-oracle-cloud-applications.html#GUID-40A60901-7D84-44BE-92C3-CC11279657A2 you need to order those services through oracle sales.
