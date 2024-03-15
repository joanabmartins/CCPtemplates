In this repository we have all the data sources that FastTrack for Azure team has been working on. 

As you navigate through the connector folders you may find different phases of development:
  * PR accepted the Master branch for Azure Sentinel repo - **Sophos Endpoint** and **Workday**
  * PR about to be submited or under review in the Azure Sentinel repo - **Jira**, **Zoom** and **Snowflake**
  * Template developed and in use by the customer; needs additional attention to make it ready for publishment - **Oracle**, **IBM Maximo**, **Trend Micro CAS**
  * Issues with supportability - **Qualys**, **Google Workspace**, **Crowdstrike**, **Salesforce**, **Ali Cloud**
  * Under development - 
  * Irrelevant working connectors - **Azure Activity** and **Google IAM**

Here is a reference list of the types of authentication, pagination and special considerations that you may find in each connector:

|                    | Authentication           | Pagination | Additional Considerations |
|--------------------|--------------------------|------------|---------------------------|
| Workday            | Oauth Authorization Code |            |                           |
| Sophos Endpoint    | Oauth Client Credentials |            |                           |
| Jira               | Basic                    |            |                           |
| Zoom               | Oauth Both ways work     |            |                           |
| Oracle             | Basic                    |            |                           |
| IBM Maximo         | Api Key                  |            |                           |
| Trend Micro CAS    | Api Key / token          |            |                           |
| Qualys             | Basic                    |            |                           |
| Crowdstrike Falcon | Oauth Client Credentials |            |                           |
| Salesforce         | Oauth Authorization Code |            |                           |
| Google Workspace   | Oauth Authorization Code |            |                           |
| Google IAM         | Oauth Authorization Code |            |                           |
| Snowflake          | Oauth Authorization Code |            |                           |
| Ali Cloud          | Ali Cloud Signature      |            |                           |