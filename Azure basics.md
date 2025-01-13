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



  



       



