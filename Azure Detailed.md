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

Now that the data is stored we move to ## Data Lake Storage Query Acceleration



