<h2>Status: This connector is working for one customer</h2>

We developed this when we were reached out by a support engineer Ryan Leng to help his customer developing this connector. 

The customer showed us how he was reaching out to the APIs through postman, we translated that to CCP and got it to work. 

We couldn't really find any documentation about this API, nor the customer. He said that IBM just informed them how to make it work. 

We didn't do anything to normalize the logs. The CCP UI definition may also need extra care, with better api access instructions, etc. 

**API Endpoints:** 

            https://< domain >.maximo.com/maximo/api/os/appauth_audit
            
            https://< domain >.maximo.com/maximo/api/os/groupuser_audit
