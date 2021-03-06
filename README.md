
# TML Blocks - Databricks Storage & Performance Analytics

The Databricks SpotApp is focused on surfacing information for billing consumption and SQL Endpoint query performance. The SpotApp consists of a number of pinboards and a workbook.

# Artifacts

## Python Script 
Python Script(SpotApp_Databricks_Python_API_Fetch.zip) to query the query the identified endpoint APIs and create the delta tables. 

## Worksheets
- Usage History Databricks 
- Query History Databricks  

worksheet formulas: 
- Usage History Databricks include a number of constants that define the price of each DBU based upon the compute category. These are prefixed with       ‘Price’.
- Query History Databricks includes a number of formulas to define if a query is identified as a ThoughtSpot index query. These are prefexed with ‘Flag     TS’.

## Liveboards 
- Databricks Query Performance 
- Databricks Query Volume
- Databricks Billing Consumption 

# Installation Instructions
 
Prior to setting up the SpotApp a data pipeline must create the tables that will be referenced via Embrace. This pipeline could be established within the Databricks platform via a workspace and scheduled job as part of the Data Science & Engineering platform. Alternatively, 3rd party tools can be leveraged to complete this. The key activities are to:
-  	extract the data from the identified APIs
-  	create delta tables that will be referenced through Embrace
-  	establish a job to refresh the data

## Databricks Workspace Archive

An example Databricks workspace archive is available as a reference (SpotApp_Databricks_Python_API_Fetch). This includes example python code to query the identified endpoint APIs and create the delta tables. Within the Data Science and Engineering platform this workspace can be scheduled as a reoccurring job. 

Within the constraints section in the example python code, a number of constants must be set. **Search for the string UPDATE to identify these.**

If you want to run this notebook yourself, you need to create a [Databricks personal access token](https://docs.databricks.com/sql/user/security/personal-access-tokens.html.) Store the access token using our secrets API, and pass it in through the Spark config, such as this: spark.pat_token {{secrets/query_history_etl/user}}, or Azure Keyvault.

## API Authentication 
These APIs require authentication. At the time of writing, billing API required basic authentication whereas the query history API used personal access tokens.
 
(https://docs.databricks.com/dev-tools/api/latest/authentication.html) <br>
(https://docs.databricks.com/sql/user/security/personal-access-tokens.html)

### Billing Usage Download API

https://docs.databricks.com/administration-guide/account-settings/billable-usage-download-api.html

***Requirements***
- Email address and password for an account owner (or account admin, if you are on an E2 account) to authenticate with the APIs. The email address and password are both case sensitive.
- Account ID. For accounts on the E2 version of the platform, get your account ID from the user profile drop-down in the account console. For non-E2 accounts, get your account ID from the account console’s Usage Overview tab. Contact your Databricks representative if you cannot find your account ID.

**Parameters**
Refer to the following link for path and query parameters.
https://docs.databricks.com/dev-tools/api/latest/account.html#operation/download-billable-usage

### Query History API
List the history of queries through SQL endpoints. You can filter by user ID, endpoint ID, status, and time range.
 
https://docs.databricks.com/sql/api/query-history.html
 
***Requirements***
Authentication is required to access this rest API.
 
Example URL Path
https://HOSTID.cloud.databricks.com/api/2.0/sql/history/queries?include_metrics=true
 
### SQL Endpoints APIs
This URL provides the name of each endpoint.
 
https://docs.databricks.com/sql/api/sql-endpoints.html
 
***Requirements***
·   	Authentication is required to access this rest API.
Example URL Path
https://HOSTID.cloud.databricks.com/api/2.0/sql/endpoints
 
 
 



## Connect with Thoughtspot and Import TML
- Log into your ThoughtSpot instance and create an Embrace connection to each the following tables.
  - endpoints
  - queries 
  - billing
 
- Combine all worksheet TML files into a ZIP file: 
  - worksheet_Manifest.yaml
  - Query History Databricks.worksheet.tml
  - Usage History Databricks.worksheet.tml

- Combine all worksheet TML files into a seperate ZIP file: 
  - Pinboard_Manifest.yaml
  - Databricks Billing Consumption.pinboard.tml
  - Databricks Query Performance.pinboard.tml
  - Databricks Query Volume.pinboard.tml
 
- Import the zipped file containing TML for the worksheets and verify that it has all been imported without any errors.
- Import the zipped file for the liveboards and verify that it has all been imported without any errors.

# Liveboard Screenshots 

### Databricks Query Volume 
<img width="1000" alt="Screen Shot 2022-04-01 at 10 49 39 AM" src="https://user-images.githubusercontent.com/102629468/161316611-e8dde8be-cf3c-41cd-8c69-1f6c1b0cc03c.png">


## Databricks Billing Consumption
<img width="1000" alt="Screen Shot 2022-04-01 at 10 49 48 AM" src="https://user-images.githubusercontent.com/102629468/161316600-00dc640a-ae54-41ea-a155-9ac2c557eb4c.png">
