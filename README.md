# Azure End to End Project 


## Architecture

![Project Architecture](./img/Project_Archiecture.png)

## Azure Services Used

### Azure Data Lake Storage Gen2 (ADLS Gen2)
Azure Data Lake Storage Gen2 is a highly scalable and secure data lake solution for big data analytics. It provides a hierarchical namespace that allows you to store data in a folder-like structure and offers features such as access control, encryption, and auditing.

### Azure SQL Database
Azure SQL Database is a fully managed relational database service in the cloud. It offers high availability, automatic backups, and built-in security features such as threat detection and data encryption.

### Azure Databricks
Azure Databricks is a fast, easy, and collaborative Apache Spark-based analytics platform optimized for Azure. It provides a notebook interface for data exploration, processing, and visualization, and integrates with other Azure services such as Azure Data Lake Storage, Azure SQL Database, and Azure Key Vault.

### Azure Key Vault
Azure Key Vault is a cloud-based service that enables you to store and manage cryptographic keys, certificates, and secrets. It provides secure access to sensitive information such as credentials, connection strings, and API keys.

### Azure Data Factory (ADF)
Azure Data Factory is a cloud-based data integration service that allows you to create, schedule, and orchestrate data workflows at scale. It provides connectors to various data sources and destinations and enables you to transform and move data between them.


## Project Flow

1. A file is dropped in the landing folder by a third-party application.
2. ADF detects the arrival of the file and triggers the pipeline.
3. The pipeline invokes the Databricks notebook.
4. The Databricks notebook fetches the SQL and Adls credentials from Azure Key Vault.
5. The Databricks notebook connects to the Azure SQL Database, fetches the schema, and validates the incoming file against the schema.
6. If the validation passes, the file is moved to the staging folder. If the validation fails, the file is moved to the rejected folder.
