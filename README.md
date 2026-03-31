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

**Architecture Diagram**

![Architecture](https://github.com/anishbaag77777/azure-data_factory-etl-project/raw/29f074dcd16ce4129de8b10a24f325596bd8355d/Data%20migration%20from%20Azure%20to%20SQL%20Server.png)
