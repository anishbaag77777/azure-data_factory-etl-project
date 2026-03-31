**Azure Data Factory ETL Pipeline – Data Migration Project**

**Overview**
This project demonstrates a metadata-driven ETL pipeline built using Azure Data Factory to migrate multiple restaurant sales datasets from Azure Data Lake to SQL Server.The pipeline is designed to be dynamic, reusable, and scalable, avoiding hardcoded values by leveraging metadata and parameterization.

**Objective**
Automate ingestion of multiple files from Azure Data Lake
Dynamically process files using a single pipeline
Load data into SQL Server tables
Reduce manual effort and improve scalability

Azure Data Lake → Azure Data Factory → SQL Server
                     →
                ForEach Loop
                     →
               Copy Data Activity

***Architecture Diagram***

![Architecture](https://github.com/anishbaag77777/azure-data_factory-etl-project/raw/29f074dcd16ce4129de8b10a24f325596bd8355d/Data%20migration%20from%20Azure%20to%20SQL%20Server.png)

**Key Components**

**Metadata-Driven Approach**

Used an array variable (metadata) to store file details
Eliminates hardcoding and improves flexibility

🔹 **ForEach Activity**
Iterates over metadata array:
@variables('metadata')

🔹 **Copy Data Activity**
Handles data movement from source to sink
Uses parameterized datasets


**Source Configuration (Azure Data Lake)**

| Parameter | Value                     |
| --------- | ------------------------- |
| Container | `@item().Outputcontainer` |
| Directory | `@item().Outputdirectory` |
| File Name | `@item().Outputfile`      |


**Sink Configuration (SQL Server)**

| Parameter  | Value                  |
| ---------- | ---------------------- |
| Schema     | `@item().sqlschema`    |
| Table Name | `@item().sqltablename` |


**Security**

Integrated Azure Key Vault for secure storage of:
   -Connection strings
   -Credentials
Ensures secure and production-ready pipeline design


**Features**

✔ Metadata-driven pipeline
✔ Dynamic file handling using @item()
✔ Reusable architecture
✔ Auto table creation in SQL Server
✔ Reduced manual effort
✔ Scalable design


**Workflow**

1)Metadata array stores file configurations
2)ForEach activity loops through each file
3)Copy Data activity:
     Reads data from Azure Data Lake
     Loads into SQL Server
4)Tables are automatically created if not present


 **Outcome**
 
Automated ingestion of multiple datasets
Built a reusable and scalable ETL pipeline
Reduced development effort for future data loads


**Learnings**

Hands-on experience with Azure Data Factory
Implemented dynamic pipelines using parameters
Learned metadata-driven design approach
Worked with Azure Key Vault for security


