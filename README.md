In this repository we have all the data sources that FastTrack for Azure team has been working on. 

As you navigate through the connector folders you may find different phases of development:
  * PR accepted the Master branch for Azure Sentinel repo - **Sophos Endpoint** and **Workday**
  * PR about to be submited or under review in the Azure Sentinel repo - **Jira**, **Zoom** and **Snowflake**
  * Template developed and in use by the customer; needs additional attention to make it ready for publishment - **Oracle**, **IBM Maximo**, **Trend Micro CAS**
  * Issues with supportability - **Qualys**, **Google Workspace**, **Crowdstrike**, **Salesforce**, **Ali Cloud**
  * Under development - 
  * Irrelevant working connectors - **Azure Activity** and **Google IAM**

Here is a reference list of the types of authentication, pagination and special considerations that you may find in each connector:

|                        | Authentication              | Pagination         | Additional Considerations                             |
|------------------------|-----------------------------|--------------------|-------------------------------------------------------|
| **Workday**            | Oauth Authorization Code    | Offset             |                                                       |
| **Sophos Endpoint**    | Oauth Client Credentials    | Next Page Token    | Multiple Endpoints                                    |
| **Jira**               | Basic                       | Offset             |                                                       |
| **Zoom**               | Oauth both grant types work | Next Page Token    | Multiple Endpoints                                    |
| **Oracle**             | Basic                       | Count Based Paging | Multiple Endpoints and environments                   |
| **IBM Maximo**         | Api Key                     | Count Based Paging | Multiple Endpoints                                    |
| **Trend Micro CAS**    | Api Key / token             | Link Header        | Multiple Endpoints                                    |
| **Qualys**             | Basic                       | Link Header        | Response in XML                                       |
| **Crowdstrike Falcon** | Oauth Client Credentials    |                    | Nested API - **not supported**                        |
| **Salesforce**         | Oauth Authorization Code    |                    | Response in XML; Nested API - **not supported**        |
| **Google Workspace**   | Oauth Authorization Code    | Next Page Token    | Complex parser - **not suited for prod**              |
| **Google IAM**         | Oauth Authorization Code    | Next Page Token    |                                                       |
| **Snowflake**          | Oauth Authorization Code    |                    |                                                       |
| **Ali Cloud**          | Ali Cloud Signature         |                    | Proprietary authentication method - **not supported** |
