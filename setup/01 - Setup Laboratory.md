# Setup Laboratory
The laboratory cointains the following resources:
- a data lake
- an Azure SQL server with AdventureWorks database sample
- an Azure Data Factory
- a Databricks Workspace

## Creating Azure SQL Database
1. Create new SQL Database. When prompted, choose SQL Deployment Option "SQL Databases":
![SQL step 1](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_1_1_choosesqldeployment.PNG)

2. Create a new Resource group for the Azure SQL Database. In the field `Resource Group` type `rg_sw_datalakehouse`

![SQL step 2](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_1_2_createresourcegroup.PNG)
3. In `Database details` section set `Database name` equal to `AdventureWorks` and create a new server
![SQL step 3](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_1_3_createsqlserver.PNG)

4. In `Server details` section set `Server name` equal to `sqldatalakehousedemo` and create a new server
![SQL step 4](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_1_4_createsqlserverdetail.PNG)
Choose SQL Authentication method, then set `Server admin login` to `sqldemologin` and choose a password.
Be sure to remember the password for further uses.

5. In `Firewall rules` section set `Add current client IP address` to `Yes`, in order to add the current IP to the whitelist.
![SQL step 4](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_1_5_configurenetworking.PNG)

6. In `Security` tab set Defender to off.
![SQL step 4](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_1_6_configuresecurity.PNG)

7. In `Additional setting` tab set under `Data source` section, the `Sample` database:
![SQL step 4](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_1_7_additionalsettings.PNG)

At the end of the step you should have two resources in the new resource group:
| Resource Type        | Resource Name              |
|----------------------|----------------------------|
| SQL Server   | sqldatalakehousedemo               |
| SQL Database | sqldatalakehousedemo/AdventureWorks|

## Creating Azure Data Lake
1. Create new Storage Account in the `rg_sw_datalakehouse` resource group:
![SQL step 1](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_2_1_createstorageaccount.PNG)
2. In `Storage account name` field set the name of the resource as `sadatalakehousedemo`:
![SQL step 1](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_2_2_setupdatalake.PNG)
Choose LRS redundancy level and Standard Performance.
3. In `Advanced` tab be sure to check `Enable hierarchical namespace` to on:
![SQL step 1](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_2_2_advanceddatalake.PNG)
Choose Create button to create the resource. Now you should have:

| Resource Type        | Resource Name              |
|----------------------|----------------------------|
| SQL Server   | sqldatalakehousedemo               |
| SQL Database | sqldatalakehousedemo/AdventureWorks|
| Azure Datalake | sadatalakehousedemo|

## Creating Azure Data Bricks Workspace
1. Create new Databricks Workspace in the `rg_sw_datalakehouse` resource group:
![SQL step 1](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_3_1_createdatabricks.PNG)
2. Set `Workspace name` to `dbdatalakehousedemo`:
![SQL step 1](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_3_2_basictab.PNG)
Choose Premium tier.

Choose Create button to create the resource. Now you should have:

| Resource Type        | Resource Name              |
|----------------------|----------------------------|
| SQL Server   | sqldatalakehousedemo               |
| SQL Database | sqldatalakehousedemo/AdventureWorks|
| Azure Datalake | sadatalakehousedemo|
| Azure DataBricks | dbdatalakehousedemo|
## Creating Azure Data Factory
1. Create new Azure Data Factory in the `rg_sw_datalakehouse` resource group. In the `Instance details` section set `Name` equal to `dfdatalakehousedemo`. Be sure to select V2 in `Version`:
![SQL step 1](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_4_1_datafactory.PNG)
2. In `Git configuration` tab select `Configure Git later`:
![SQL step 1](https://github.com/villalaura/sw_datalakehouse_demo/raw/main/media/step_4_2_dfgit.PNG)
3. Choose Create button to create the resource. Now you should have:

| Resource Type        | Resource Name              |
|----------------------|----------------------------|
| SQL Server   | sqldatalakehousedemo               |
| SQL Database | sqldatalakehousedemo/AdventureWorks|
| Azure Datalake | sadatalakehousedemo|
| Azure DataBricks | dbdatalakehousedemo|
| Azure Data Factory | dfdatalakehousedemo|

