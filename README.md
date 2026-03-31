**Azure Data Factory ETL Pipeline – Data Migration Project**

**Overview**
This project demonstrates a metadata-driven ETL pipeline built using Azure Data Factory to migrate multiple restaurant sales datasets from Azure Data Lake to SQL Server.The pipeline is designed to be dynamic, reusable, and scalable, avoiding hardcoded values by leveraging metadata and parameterization.

**Objective**
Automate ingestion of multiple files from Azure Data Lake
Dynamically process files using a single pipeline
Load data into SQL Server tables
Reduce manual effort and improve scalability

**Architecture**

Azure Data Lake → Azure Data Factory → SQL Server
                     →
                ForEach Loop
                     →
               Copy Data Activity

![Architecture](images/architecture.png)
