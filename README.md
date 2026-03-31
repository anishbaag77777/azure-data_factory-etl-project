# **Azure Data Factory ETL Pipeline – Data Migration Project**

# **Overview**
This project demonstrates a metadata-driven ETL pipeline built using Azure Data Factory to migrate multiple restaurant sales datasets from Azure Data Lake to SQL Server.The pipeline is designed to be dynamic, reusable, and scalable, avoiding hardcoded values by leveraging metadata and parameterization.

# **Objective**
The goal of this project is to build a dynamic and scalable ETL pipeline that:

• Reads multiple restaurant sales files from Azure Data Lake

• Processes them using a single reusable pipeline

• Loads data into SQL Server tables dynamically

• Eliminates hardcoding using metadata-driven design


Azure Data Lake → Azure Data Factory → SQL Server
                     →
                ForEach Loop
                     →
               Copy Data Activity

# **Architecture Diagram**

![Architecture](https://github.com/anishbaag77777/azure-data_factory-etl-project/raw/29f074dcd16ce4129de8b10a24f325596bd8355d/Data%20migration%20from%20Azure%20to%20SQL%20Server.png)

# **Key Components**

## **Metadata-Driven Approach**

### 1. Metadata Variable (Core Logic)

A pipeline variable named metadata is created with:

Type: Array
Purpose: Store configuration for multiple files

####  Why this is important:?

Instead of creating multiple pipelines, you define everything in one place and reuse it.

### 2. ForEach Activity

####  Configuration:

Items:
@variables('metadata')

#### What it does:?

Iterates through each object (file details) in the metadata array
Runs the Copy Data activity for each file

### 3. Copy Data Activity

This is the main ETL component where data movement happens.
Handles data movement from source to sink
Uses parameterized datasets


### **Source Configuration (Azure Data Lake)**

| Parameter | Value                     |
| --------- | ------------------------- |
| Container | `@item().Outputcontainer` |
| Directory | `@item().Outputdirectory` |
| File Name | `@item().Outputfile`      |

#### Explanation:

Each time the loop runs, it picks a different file from Azure Data Lake.


### **Sink Configuration (SQL Server)**

| Parameter  | Value                  |
| ---------- | ---------------------- |
| Schema     | `@item().sqlschema`    |
| Table Name | `@item().sqltablename` |

#### Explanation:

Data is loaded into different tables dynamically

Table names come from metadata

### 4. Auto Table Creation

 #### Option Used:

### Auto Create Table

#### What it does:

Automatically creates SQL tables if they don’t exist

Uses source file schema

#### Benefit of using it:

No need to manually create tables in SQL Server

# **Security**

Integrated Azure Key Vault for secure storage of:
   -Connection strings
   -Credentials
Ensures secure and production-ready pipeline design


# **Key Features of This Project**

Metadata-driven architecture

Fully dynamic pipeline (no hardcoding)

Reusable design for multiple files

 Scalable for future datasets
 
 Reduced manual effort
 
 Clean and maintainable ETL pipeline


# End-to-End Workflow

Metadata variable stores all file configurations

ForEach activity loops through metadata

For each iteration:

  • Source dataset picks file dynamically
  
  • Copy activity transfers data

Sink dataset loads into SQL Server

Tables are created automatically


 # **Outcome**
 
Automated ingestion of multiple datasets
Built a reusable and scalable ETL pipeline
Reduced development effort for future data loads


# **Learnings**

Hands-on experience with Azure Data Factory
Implemented dynamic pipelines using parameters
Learned metadata-driven design approach
Worked with Azure Key Vault for security


