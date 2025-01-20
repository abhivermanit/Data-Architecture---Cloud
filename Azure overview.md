Batch vs Stream Data  

Batch - Start and end date known, process high volume of data
        takes long time to process data 
        payement processing
        

Stream - No end defined 
         Data is processed on arrival 
         takes less time to process comparatively 
         real time message ingestion


OLTP vs OLAP 

OLTP - faster processing 
       MySQL, oracle 
       traditional RDBMS
       data processing 
       It’s also used for Online banking, Online airline ticket booking, sending a text message, add a book to the shopping cart.

OLAP - Data Warehousing
       data collected from multiple resources - so that is why warehouse is needed
       complex query
       Azure synapse analytics(ASA) - Petabyte Data Warehouse
       data analysis


Data Lake vs Data Warehouse 

- storage cost low
- schema on read (The schema is defined after the data is loaded)
- All types of data
- for DE, DS and Developers

  Warehouse

  - structured data only (rows and columns)
  - schema on write
  - for data analysts
  - querying result takes time
 

Big Data Architecture 


From data sources there is 2 things
- Data storage -- Batch processing -- 
- Real time message ingestion -- Stream processing

  *** From multiple data sources data is ingested into the data storage for batch processing, from here we get the word ingestion

from here on it goes to the analytical data store and reporting

Data storage 
- Blob storage
- Data Lake
- Cosmos DB
- SQL Database

Real Time Messaging 
- Kafka
- Event Hubs

  Stream Processing
  - Spark Streaming
  - Spark Analytics

Batch Processing 
- U SQL
- Hive
- Spark

Azure Basic Services :- 

The basic thing in cloud computing is that they provide you a virtual way to store on a cloud/ different machine

In basic Azure Services we have the Azure CLI and Azure Cloud Shell and then we can create a VM from that 

*** Whenever you create an account, you're supposed to create and manage the storage(which blob, subblob type etc)

AZURE STORAGE :---

Azure Blob, Azure Data Lake Storage Gen2 (ADLS), Azure Queue, Azure Table

Azure SQL Database for Relational Data storage

Azure CosmosDB for NoSQL Data storage


AZURE STORAGE SOLUTIONS 
- SQL
- NO SQL

  Within NO SQL we have IAAS and PAAS

  Within PAAS
  - Azure Storage
  - Cosmos DB
  - Data Lake
 
    Azure Storage
    - Blob
    - Table
    - File
    - Queue
   
To access these storage accounts we can access them via 
- Rest APi
- Azure CLI
- SDKs

  BLOB (Binary Large Object)

  - Massive amounts of unstructured data
  - no restriction on particular file type
  - data access(HTTPS)
  - cheapeast data storage
  - object is stored in flat and not hierarchial structure


Container is basically like a directory and a collection of blobs

  Table 
  - Semi Structured/ No SQL
  - Denormalized data
  - Each row is uniquely identified by a key
  - No relation among them, no foreign key
  - While insertion - Row key and partition key is required
  - Next version of table is Cosmodb
  - No foreign key instead we have Key/value pair, partition key and row key

Azure Queue Storage :-
- Message queue system
- Storage large number of message
- Buffer system between 2 applications for asynchronus communication

Azure File Share :-
- Serverless sharing
- file sharing in cloud

Azure Disk Storage :-
-Block storage for Azure VM
- Store data on the VM


Azure Data Lake Gen2
- massive data in row format
- no cleaning required like warehouse
- bult on top of azure blob storage (Data Blob + Azure Data Lake Gen1)
- Hierarchial data structure (not available in blob)
- Hadoop-compatible access


Managing Azure Storage using Azure CLI :-

So to summarize whenever azure storage is created it is done in following layers. 
- basic configuration
- create group
- create storage account
- container and blob
- azure queue
- azure table
       

Azure Bash 

- az login
- az group list -o json (retrieve a list of resource groups in your Azure subscription) (-o is the format, here it is JSON)
- az configure
- az group create --help (this will give all the commands needed)
- az storage
- az storage container -n
- az storage blob
- az storage blob --help (all commands)
- az storage delete blob
