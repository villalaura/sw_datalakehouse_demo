# Preparing SQL Database
A Watermark will be used to ingest table data from SQL Database. This steps is needed to reset the watermarks for the existing tables, to be able to run the first ingestion.

1. Login to SQL Server database `AdventureWorks` and run this code to create the Watermark Table:
    ```sql
    CREATE TABLE [dbo].[WatermarkTable](
	[TableName] [varchar](100) NOT NULL,
	[WatermarkValue] [datetime] NULL,
    CONSTRAINT [PK_WatermarkTable] PRIMARY KEY CLUSTERED 
    (
	[TableName] ASC
    )WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    ```
2. Fill the Watermark Table with the command. This will set the watermark for the main tables of the database to 1/1/2000:

    ```sql
    SELECT QUOTENAME(table_schema)+'.'+QUOTENAME(table_name) AS TableName, '2000-01-01' FROM 
    information_Schema.tables WHERE table_name not in 
    ('watermarktable','buildversion','errorlog','database_firewall_rules','ipv6_database_firewall_rules',
    'vGetAllCategories','vProductAndDescription','vProductModelCatalogDescription')
    ```
    
# Preparing the Datalake
We'll setup the Datalake creating the three containers:
| Container name | Description
|----------------------|----------------------------|
| bronze| This is the container that will be used in the ingestion pipeline               |
| silver| This is the container that will be used in the curation pipeline               |
| gold| This is the container that will be used in the aggregation pipeline               |

To accomplish this:
1. In the resource `sadatalakehousedemo` choose Containers in the left menù
2. Click on '+ Container' to add a new container
3. In the field `Name` type `bronze` and leave `Private` in the access level. Then click `Create`
![Preparing dl](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/preparing_datalake_1.PNG)
4. Repeat the step number 2, 3 for the silver and the gold containers
5. You should have three cointainers:
![Preparing dl](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/preparing_datalake_2.PNG)