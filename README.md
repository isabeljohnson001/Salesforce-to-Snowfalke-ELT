# Salesforce to Snowflake Data ELT Pipeline
This project demonstrates building an end-to-end ELT pipeline using Azure Data Factory to transfer data from Salesforce to Snowflake. It involves reading table names from an Excel file, copying data to Parquet files in Azure Blob Storage, and then loading and transforming these files into Snowflake tables using a stored procedure.

## Prerequisites
- API permissions must be enabled in Salesforce.

- Azure Data Factory and Resource group access.

- Azure Key Vault (recommended for production systems).

### Architecture Overview
Setting up a Linked Service to Salesforce
Create a Linked Service to Salesforce:
Navigate to the Manage tab in your Azure Data Factory or Synapse workspace.
Select Linked Services > New.
Search for and select the Salesforce connector.
Configure the service details, including authentication method. For testing, use a password; for production, integrate with Azure Key Vault.
Test the connection, then click Create.
Creating a Data Pipeline
Initiate a New Pipeline:

Go to Author, and select New Pipeline.
Use the Copy Data tool for an easier setup or proceed manually for more customization.
Configure Source and Target:

Source: Configure the Salesforce connector with the necessary queries or table selections.
Target: Set up Snowflake as the target, providing credentials and destination details.
Handle Excel Input:

Use the Excel file as an input to dynamically generate a list of Salesforce table names for data extraction.
Implement a For-Loop activity to iterate through each table name and trigger data copy tasks.
Data Copy and Transformation:

Data from Salesforce is copied to Parquet files stored in Azure Blob Storage.
Parquet files are then transformed and loaded into Snowflake tables using a stored procedure within a Script Activity.
Deployment
Follow Azure Data Factory's deployment guidelines to move your pipeline from development to production.
Security
Ensure all connections are secured and credentials are stored safely, preferably using Azure Key Vault.
Troubleshooting
Monitor pipeline runs in the Azure Data Factory dashboard, checking for errors or failed activities.
