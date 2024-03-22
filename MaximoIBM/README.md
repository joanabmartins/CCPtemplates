<h2>Status: This connector is working for one customer</h2>

We developed this when we were reached out by a support engineer Ryan Leng to help his customer developing this connector. 

The customer showed us how he was reaching out to the APIs through postman, we translated that to CCP and got it to work. 

We couldn't really find any documentation about this API, nor the customer. He said "Our internal development team said these API endpoints are custom-built for our organisation, but that they used 'standard Maximo processes' to create these APIs.  I don't have access to the Maximo application itself, but I believe there may still be value in packaging this if other organisations create these API endpoints that serve the same data.  I'm happy to discuss further with the relevant teams on Microsoft's side for packaging."

We didn't do anything to normalize the logs. The CCP UI definition may also need extra care, with better api access instructions, etc. 

**API Endpoints - apparently these are custom to the customer to whom we developed this with:** 

            https://< domain >.maximo.com/maximo/api/os/appauth_audit
            
            https://< domain >.maximo.com/maximo/api/os/groupuser_audit
