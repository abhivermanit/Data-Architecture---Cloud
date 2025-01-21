# Azure SQL Database

It has both compute + storage (VM to run on and blob to store on)

## Azure SQL Family 
- IAAS - SQL server on Azure VM
- PAAS - Azure SQL database


## Azure SQL Database 
- Single database
- Elastic Pool
- Azure SQL Managed Instance

All these different databases allow to operate according to the user expectations. When someone has a on premise server then also if they want to use then Azure SQL managed instance.
Single database is fully managed and organized by Azure 


## File Types in Azure
- CSV, TSV, PSV
- JSON (JavaScript Object Notation): API responses in JSON format.
- Apache Avro: Storing log data in distributed systems.
- Apache Parquet: Storing large datasets in a data warehouse for fast read performance.

## Design for Maximum Query Performance

To optimize the query performance, inspect the Bytes read/write by the query. 

The 2 ways to optimize are:-
- CPU intensity of the query
- Indexing level of the data solution

Non-relational systems:- (e.g., Azure Cosmos DB) index all JSON properties by default, customize indexing as needed.

Relational systems:- (e.g., SQL databases) use primary key columns for partitioning and indexing.

Example: Creating indexes on frequently queried columns to speed up query performance.



# Data Lake

enable the hierarchical namespace, while creating a data lake account, this will allow creation of folders and sub-folders which will enhance the query speed.

Directories and files created:- manage their access control lists (ACLs), similar to Linux-like permissions.

ACLs can be tied to Azure Active Directory users, groups, and service principals. AAD includes SSO(Single Sign-On) and MFA(Multi-Factor Authentication)

Now that the data is stored we move to **Data Lake Storage Query Acceleration**

***Azure Data Explorer***:- This is a part of storage query acceleration, a tool for non-relational big data analytics. Uses Kusto Query Language (KQL) for querying.
Allows running massively parallel queries without managing underlying compute.


# Part-2 Design for Data Pruning
## 2.1 Design a Folder Structure for Data Transformation
**Data Pruning**
- Data Pruning is the process of removing unnecessary or irrelevant data from a dataset.
- Removing irrelevant data to accelerate queries and improve signal-to-noise ratio.
- signal-to-noise ratio, this just means that lower the noise more the signal so better just a symbolic thing
- Examples: Removing incomplete data, invalid data, and non-contributory columns or rows.
- Example: Dropping columns with more than 50% missing values.

**Data Partitioning**
- Organizing data in a way that facilitates easier querying and management.
- In Azure Data Lake Storage Gen 2, use hierarchical file systems and query acceleration features.
- In relational databases (e.g., Azure Synapse Analytics SQL pool), horizontally partition large tables based on columns like date.
- Example: Partitioning sales data by month and archiving old partitions.

**In-memory Processing**
- In non-relational systems (e.g., Azure Databricks, Azure Synapse Analytics Apache Spark Pools), processing happens in memory.
- Use Apache Spark to repartition, reorganize, and prune data in memory.
- Example: Using Spark DataFrames to filter out unwanted data before analysis.

## 2.2 Design a Distribution Strategy
**Azure Synapse Analytics**
- Core feature: 60 distributions (virtual machines) for massively parallel processing (MPP).

  **Types of distribution methods**
    **Hash Distribution** : - Use for tables larger than 2GB with regular I/O.

- Synapse creates a cryptographic hash of a column to distribute rows.

- Combined with clustered columnstore indexes for fast query performance.

- Example: Distributing sales data by customer ID for parallel processing.





