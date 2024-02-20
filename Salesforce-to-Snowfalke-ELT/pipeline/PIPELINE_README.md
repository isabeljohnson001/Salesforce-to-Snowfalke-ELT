# ADF.ETL.Salesforce

## Data Snapshot

Excel is selected as the input to provide a list of table names for data loading from Salesforce.The table name is passed a parameter to Object Api in Copy Data Activity. A for-loop iterates through each table name, copying data from Salesforce to Parquet files stored in Blob Storage, which acts as the source. These Parquet files are then transformed and loaded into Snowflake tables using a stored procedure in a Script Activity.

## Update latest data to existing tables

The table name is passed a parameter to query method in Copy Data Activity with value as below.This value was constructed using the string builder.Data flow remains same.

```
"query": {
										"value": "@concat('select * from ',variables('TableName'),' WHERE CAST(LastModifiedDate AS DATE) >= ''',variables('Yesterday_Date'),''' ORDER BY LastModifiedDate desc;')",
										"type": "Expression"
									},
									"readBehavior": "queryAll"
```                                    