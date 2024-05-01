
# Databricks Storage and Performance SpotApp

The Databricks SpotApp is focused on surfacing information for billing consumption and SQL Endpoint query performance. The SpotApp includes a number of pinboards and a workbook.

SpotApps are ThoughtSpot’s out-of-the-box solution templates built for specific use cases and data sources. They utilize ThoughtSpot Modeling Language (TML) Blocks, which are pre-built pieces of code that are easy to download and implement directly from the product.

The Databricks Storage and Performance SpotApp mimics the Databricks data model. When deployed, it creates several Worksheets, Answers, and Liveboards based on your Databricks data in your cloud data warehouse.

This is a sample Liveboard, created after you deploy the Databricks Storage and Performance SpotApp:

Use the Databricks Storage and Performance SpotApp to manage costs and investigate query performance. Track how and where your users consume Databricks Units (DBUs), and investigate latency issues with database queries. You can also review your tables' Z-Ordering.

## Prerequisites

Before you can deploy the Databricks Storage and Performance SpotApp, you must complete the following prerequisites:

- **Review Required Data**: Examine the required tables and columns for the SpotApp.
- **Ensure Column Compatibility**: Make sure that your columns match the required column type listed in the schema for your SpotApp.
- **Obtain Credentials**: Acquire credentials and SYSADMIN privileges to connect to Databricks. The cloud data warehouse must contain the data ThoughtSpot will use to create Answers, Liveboards, and Worksheets. Refer to the connection reference for Databricks for information about required credentials.
- **Unique Connection Name**: Ensure that the connection name for each new SpotApp is unique.
- **Administrator Access to Databricks**: Maintain administrator access to manage Databricks resources.
- **Access to Databricks Tables**: Ensure access to the following Databricks tables in your cloud data warehouse:
  - `ENDPOINTS`
  - `QUERIES`
  - `BILLING`

### Run Python Script

Execute the following Python script on your Databricks instance to load the Databricks data into tables. Modify any parts of the script that require updates, such as the hostid, accountid, and authorization token.

Python code can be found here: Databricks_PythonScript.py

## Deploy the SpotApp

After you have downloaded the Zip file and verified its contents, follow these steps:

1. Log into your ThoughtSpot instance and create an Embrace connection to all of the relevant views.
2. Import the TML for the worksheets and verify that it has all been imported without any errors.
3. Import the TML for the pinboard and verify that it has all been imported without any errors.
4. You are ready to start searching your Databricks data!

For detailed instructions on how to import TML files, refer to the [ThoughtSpot documentation](https://docs.thoughtspot.com/software/latest/tml-import-export-multiple).

# Liveboard Screenshots 

### Databricks Query Volume 
<img width="1000" alt="Screen Shot 2022-04-01 at 10 49 39 AM" src="https://user-images.githubusercontent.com/102629468/161316611-e8dde8be-cf3c-41cd-8c69-1f6c1b0cc03c.png">


## Databricks Billing Consumption
<img width="1000" alt="Screen Shot 2022-04-01 at 10 49 48 AM" src="https://user-images.githubusercontent.com/102629468/161316600-00dc640a-ae54-41ea-a155-9ac2c557eb4c.png">
