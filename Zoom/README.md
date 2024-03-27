<h2>Zoom Resport Status: Developed like the old connector, which raises a few questions</h2>

There is already a function connector supporting Zoom integration. 
It connects to 6 different endpoints: Daily Usage Reports, Active/Inactive Host Reports, Telephone Report, Cloud Recording Usage Reports, Operation Logs Report, Sign In/Sign Out Activity Report.

These APIs have different response schemas, so we don't agree with having all of them sending logs to the same table like the previous connector. We separated them into 6 different tables. 

These APIs cannot be filtered by hour or minutes, the maximum we can filter is by day (in some of them), so we don't agree with the existing connector that is querying every hour, it generated a loooot of repeated logs. In some cases we could query every 5 minutes and then do a transformation to don't ingested repeated data. In other cases, maybe doesn't make sense to call that api endpoint at all, we should check with existing customers using the connector. **It needs to be further dicussed**. 

Right now, this CCP connector is also created to pull every 1 hour, ingesting repeated data.

It is still missing a parser to connect the old table with the new table. The old parser is not the most well constructed one (it uses a feel called Dates, which is not recommended), and as I think this connector is general should get a second thought, I didn't really go ahead to develop the parser, following the old schema.

  
<h3>Authentication details</h3>

Zoom supports 2 types of Oatuh authentication. 

* Generic zoom oauth application by **code authorization** - After some research that included contacting Zoom support, we realised that the authentication token and refresh tokens got revoked every time a new authentication token got issued. 
As there were 6 different rules and each one of them was using their own authentication token, every time one connects it was breaking the connection established by the other rule. 
This was what we observed and how Yonggang confirmed it works. Maor didn't agree. I think it is worth discussing this further to understand how the authentication token is shared between rules.
In any case, even if the authentication token and refresh tokens get to be shared between rules, using thist type of authentication could be very easily compromised. 
If I reached the API through postman or tried to use the connector in a different workspace, using the same credentials, I would break the original connector.

* Server to Server oauth application - The one we decided to go with. This application has the peculiarity of using grant type account credentials, instead of the regular client credentials. 
Once again we had difficulties interpreting the issues that we were seeing. Through postman the API calls were working fine, we would add the grant_type and account_id parameters in the request body to get the token, 
and everything worked. However, when we translated this to CCP it didn't work. We added these parameters in the TokenEndpointQueryParameters, but the connector wouldn't connect.
We ended up finding a workaround, if we put these parameters directly in the URL,
it didn't matter if we were adding them in the request body or not, the API was still issuing a valid token, and we were able to get logs.
So, we ended up adding them directly in the token endpoint url, instead on the body as they should, and as we saw in Postman it should work, and with this workaround this connector is working fine.

<h3>Template</h3>

As discussed above the template includes 6 rules. Each one sending logs to its own table.

It pulls every 1 hours which raises concern for repeated logs, but it was how the old connector was working.

<h3>Parser and transformations</h3>

I just did basic transformations to avoid using forbidden fields. I didn't transform fields to accomodate old schema and I didn't develop the old parser to include the new tables. As I think this whole connector should be double checked, I thought this should be left to be developed after that.

<h3>Documentations </h3>

About Server 2 Server authentication: https://developers.zoom.us/docs/internal-apps/s2s-oauth/

About API Endpoints: https://developers.zoom.us/docs/api/rest/reference/zoom-api/methods/#tag/Reports


  
<h3>Testing considerattions</h3>

To use the Zoom API we need a Zoom pro account. The only way I discovered to get access to a trial of a zoom pro account, was by installing the Zoom Mobile App. 
After installing the app in my mobile, it asked if I wanted to try the pro plan.

