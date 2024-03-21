In this repository we have all the data sources that FastTrack for Azure team has been working on. 

As you navigate through the connector folders you may find different phases of development:
  * Published - **Sophos Endpoint** and **Workday**
  * PR under review - **Jira**
  * Developed to work equally to previous connector, but we may want to change how it works - **Zoom**
  * Template developed and in use by the customers; needs additional attention to make it ready for publishment - **Oracle**, **IBM Maximo**, **Trend Micro CAS**
  * Issues with supportability - **Qualys**, **Google Workspace**, **Crowdstrike**, **Salesforce**, **Ali Cloud**
  * Under development - **Snowflake**
  * Irrelevant connectors that work - **Azure Activity** and **Google IAM**

Here is a reference list of the types of authentication, pagination and special considerations that you may find in each connector:

|                        | Authentication              | Pagination         | Additional Considerations                             |
|------------------------|-----------------------------|--------------------|-------------------------------------------------------|
| **Workday**            | Oauth Authorization Code    | Offset             | Uses ASIM audit table                                 |
| **Sophos Endpoint**    | Oauth Client Credentials    | Next Page Token    | Multiple Endpoints                                    |
| **Jira**               | Basic                       | Offset             | Multiple environments                                 |
| **Zoom**               | Oauth both grant types      | Next Page Token    | Multiple Endpoints                                    |
| **Oracle**             | Basic                       | Count Based Paging | Multiple Endpoints and environments.                  |
| **IBM Maximo**         | Api Key                     | Count Based Paging | Multiple Endpoints                                    |
| **Trend Micro CAS**    | Api Key / token             | Link Header        | Multiple Endpoints                                    |
| **Qualys**             | Basic                       | Link Header        | Response in XML                                       |
| **Crowdstrike Falcon** | Oauth Client Credentials    |                    | Nested API - **not supported**                        |
| **Salesforce**         | Oauth Authorization Code    |                    | Response in XML Nested API - **not supported**        |
| **Google Workspace**   | Oauth Authorization Code    | Next Page Token    | Multiple Endpoints and environments. Complex parser - **not suited for prod**              |
| **Google IAM**         | Oauth Authorization Code    | Next Page Token    |                                                       |
| **Snowflake**          | Oauth Authorization Code    |                    |                                                       |
| **Azure Activity**     | Oauth Client Credentials    |                    |                                                       |
| **Ali Cloud**          | Ali Cloud Signature         |                    | Proprietary authentication method - **not supported** |
