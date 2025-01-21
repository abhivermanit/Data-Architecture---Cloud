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


**Hash Distribution** :

- Hash Distribution is a method used in databases to evenly distribute data across multiple nodes or partitions based on a hash function.
  This helps improve performance and balance the load when processing queries.
  
- Use for tables larger than 2GB with regular I/O.

- Synapse creates a cryptographic hash of a column to distribute rows.

- Combined with clustered columnstore indexes for fast query performance.

- Example: Distributing sales data by customer ID for parallel processing.

- How It Works:
Hash Function: A hash function takes a specific column's value (like an ID) and converts it into a hash value.
Distribution: The hash value determines which node or partition the data will go to. This ensures that data is spread out evenly.

- Example:
Imagine you have a table of customer orders, and you want to distribute the data based on the customer_id:

If you have 4 nodes (Node 1, Node 2, Node 3, Node 4), the hash function might assign:
customer_id 1 → Node 1
customer_id 2 → Node 2
customer_id 3 → Node 3
customer_id 4 → Node 4
customer_id 5 → Node 1 (and so on)
Benefits:
Balanced Load: Helps prevent any single node from becoming a bottleneck.
Improved Performance: Queries can be processed in parallel across multiple nodes, speeding up data retrieval.
In short, hash distribution helps manage data efficiently in a distributed database system(a type of database that is spread across multiple locations or servers)!


**Round-Robin Distribution**
- Ideal for temporary staging tables or data loads.

- Distributes rows evenly across all distributions without computing hashes.

- Example: Staging table for initial data load before further processing.

**Replication**
- Use for small tables (<2GB) requiring fast queries.

- Replicates all rows to every distribution, avoiding the need to access other distributions during queries.

- Example: Lookup tables that are frequently joined with large fact tables.











