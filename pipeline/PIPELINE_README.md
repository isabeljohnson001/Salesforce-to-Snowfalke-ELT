# ADF.ETL.Salesforce


Excel is selected as the input to provide a list of table names for data loading from Salesforce. A for-loop iterates through each table name, copying data from Salesforce to Parquet files stored in Blob Storage, which acts as the source. These Parquet files are then transformed and loaded into Snowflake tables using a stored procedure in a Script Activity.
