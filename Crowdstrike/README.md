<h2>Status: CCP NOT SUPPORTED</h2>


We have been hearing from customers that don't want to use a data collection solution based on AWS S3s, nor on AMA. So, we tried to use CCP just directly reach the Crowdstrike API and get the logs. 

As we investigated the Crowdstrike APIs with the customer we discovered that we couldn't actually just call one API to get the logs. The way the API works is by calling one API to get some IDs, and then call the logs API with those IDs.

<h3>Example to get detection logs:</h3>

          Get https://api.crowdstrike.com/detects/queries/detects/v1

**Authentication**: Oauth, Client credentials, https://api.crowdstrike.com/oauth2/token

**Response:** list of IDs

            Post https://api.crowdstrike.com/detects/entities/summaries/GET/v1
  
**Body:** {"ids": [ "ldt:GUID:int", "ldt:GUID:int"]}

**Authentication:** Oauth, Client credentials, https://api.crowdstrike.com/oauth2/token

**Response**: logs

<h3>Example to get incident logs:</h3>

          Get https://api.crowdstrike.com/incidents/queries/incidents/v1

**Authentication:** Oauth, Client credentials, https://api.crowdstrike.com/oauth2/token

**Response:** list of ids

          Post https://api.crowdstrike.com/incidents/entities/incidents/GET/v1

**Body:** {"ids": [ "inc:GUID:GUID"]}

**Authentication:** Oauth, Client credentials, https://api.crowdstrike.com/oauth2/token

<h3>Template</h3>

I quickly tested it with CCP, by hardcoding some IDs in the template. It doens't make sense, it is always getting the logs for the same IDs, just wanted to test authentication, etc.

<h3>Documentation</h3>

I added in this directory a PDF with the docs that the customer provided to us for the Crowdstrike API.
