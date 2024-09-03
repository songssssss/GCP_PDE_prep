### Question 15

Your globally distributed auction application allows users to bid on items. Occasionally, users place identical bids at nearly identical times, and different application servers process those bids. Each bid event contains the item, amount, user, and timestamp.
You want to collate those bid events into a single location in real time to determine which user bid first.

What should you do?
Create a file on a shared file and have the application servers write all bid events to that file. Process the file with Apache Hadoop to identify which user bid first.
Have each application server write the bid events to Cloud Pub/Sub as they occur. Push the events from Cloud Pub/Sub to a custom endpoint that writes the bid event information into Cloud SQL.
Set up a MySQL database for each application server to write bid events into. Periodically query each of those distributed MySQL databases and update a master MySQL database with bid event information.
Have each application server write the bid events to Google Cloud Pub/Sub as they occur. Use a pull subscription to pull the bid events using Google Cloud Dataflow. Give the bid for each item to the user in the bid event that is processed first.

From <https://www.passnexam.com/google/professional-data-engineer/2> 




### Question 18

Your infrastructure includes a set of YouTube channels. You have been tasked with creating a process for sending the YouTube channel data to Google Cloud for analysis. You want to design a solution that allows your world-wide marketing teams to perform ANSI SQL and other types of analysis on up-to-date YouTube channels log data.

How should you set up the log data transfer into Google Cloud?
Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Multi-Regional storage bucket as a final destination.
Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Regional bucket as a final destination.
Use BigQuery Data Transfer Service to transfer the offsite backup files to a Cloud Storage Multi-Regional storage bucket as a final destination.
Use BigQuery Data Transfer Service to transfer the offsite backup files to a Cloud Storage Regional storage bucket as a final destination.


Answer is Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Multi-Regional storage bucket as a final destination.

Destination is GCS and having multi-regional so A is the best option available.

Even since BigQuery Data Transfer Service initially supports Google application sources like Google Ads, Campaign Manager, Google Ad Manager and YouTube but it does not support destination anything other than bq data set



Question 19

You are designing storage for very large text files for a data pipeline on Google Cloud. You want to support ANSI SQL queries. You also want to support compression and parallel load from the input locations using Google recommended practices.

What should you do?
Transform text files to compressed Avro using Cloud Dataflow. Use BigQuery for storage and query.
Transform text files to compressed Avro using Cloud Dataflow. Use Cloud Storage and BigQuery permanent linked tables for query.
Compress text files to gzip using the Grid Computing Tools. Use BigQuery for storage and query.
Compress text files to gzip using the Grid Computing Tools. Use Cloud Storage, and then import into Cloud Bigtable for query.

From <https://www.passnexam.com/google/professional-data-engineer/2> 



In Google BigQuery, as well as in many other database systems, tables are categorized into **temporary tables** and **permanent tables** based on their lifecycle and use cases. Here’s a detailed explanation of each type:

### **Temporary Tables**

**Temporary tables** are tables that exist only for the duration of a single session or query. They are used for intermediate data storage during query execution and are automatically deleted when the session or query ends.

#### **Characteristics of Temporary Tables:**
- **Scope**: Temporary tables are specific to a session or a single query execution. They are not visible outside the session in which they are created.
- **Lifetime**: They are automatically removed once the session or query finishes. In BigQuery, temporary tables are dropped at the end of the query execution if created within a query.
- **Usage**: Useful for intermediate results or staging data within complex queries. They help manage and optimize the performance of large and complex SQL operations.
- **Storage Costs**: No additional storage costs are incurred because temporary tables are not stored permanently.

#### **Creating Temporary Tables in BigQuery:**
```sql
-- Temporary table created within a query
WITH temp_table AS (
  SELECT *
  FROM `mydataset.mytable`
  WHERE condition = 'some_value'
)
SELECT *
FROM temp_table;
```
In this example, `temp_table` exists only for the duration of this query and is not stored in BigQuery's permanent storage.

### **Permanent Tables**

**Permanent tables** are tables that persist beyond the current session or query execution. They are stored in BigQuery’s dataset and can be queried, updated, or deleted as needed.

#### **Characteristics of Permanent Tables:**
- **Scope**: Permanent tables exist in a dataset and are available across different sessions and queries. They are accessible to anyone with the appropriate permissions.
- **Lifetime**: They remain in the dataset until explicitly deleted. They are intended for long-term storage of data.
- **Usage**: Ideal for storing data that needs to be retained for ongoing use, reporting, and analysis.
- **Storage Costs**: You incur storage costs based on the amount of data stored in these tables. This includes costs for data storage, as well as any additional costs for querying and processing.

#### **Creating Permanent Tables in BigQuery:**
```sql
-- Creating a permanent table by querying data and saving it
CREATE TABLE `mydataset.my_permanent_table` AS
SELECT *
FROM `mydataset.source_table`
WHERE condition = 'some_value';
```
In this example, `my_permanent_table` is created in the dataset `mydataset` and will persist until it is manually deleted.

### **Summary**

- **Temporary Tables**:
  - Exist only for the duration of a session or query.
  - Useful for intermediate data storage and processing.
  - Automatically deleted after use.
  - No additional storage costs.

- **Permanent Tables**:
  - Persist beyond the session or query.
  - Suitable for long-term data storage and ongoing queries.
  - Remain until explicitly deleted.
  - Incurs storage costs based on data volume.

Both types of tables play important roles in managing and processing data effectively in BigQuery, depending on the use case and requirements.




Question 21

You are designing storage for two relational tables that are part of a 10-TB database on Google Cloud. You want to support transactions that scale horizontally.

You also want to optimize data for range queries on non-key columns.

What should you do?
Use Cloud SQL for storage. Add secondary indexes to support query patterns.
Use Cloud SQL for storage. Use Cloud Dataflow to transform data to support query patterns.
Use Cloud Spanner for storage. Add secondary indexes to support query patterns.
Use Cloud Spanner for storage. Use Cloud Dataflow to transform data to support query patterns.

From <https://www.passnexam.com/google/professional-data-engineer/3> 




Google Cloud Spanner and Google Cloud SQL are two managed database services offered by Google Cloud, each designed for different use cases and providing different features. Here’s a detailed comparison of the two:

### **Google Cloud Spanner**

**Overview**:
- **Type**: Fully managed, scalable, and globally distributed relational database.
- **Primary Use Cases**: Large-scale, mission-critical applications that require high availability, strong consistency, and horizontal scalability.

**Key Features**:
1. **Scalability**:
   - **Horizontal Scaling**: Cloud Spanner can scale out across multiple nodes and regions seamlessly, handling large amounts of data and high transaction volumes.
   - **Global Distribution**: Supports multi-region and global deployment with automatic replication and strong consistency across locations.

2. **Consistency and Availability**:
   - **Strong Consistency**: Provides strong consistency and ACID (Atomicity, Consistency, Isolation, Durability) properties across distributed nodes.
   - **High Availability**: Built-in high availability and disaster recovery with automatic failover and replication.

3. **Data Model**:
   - **Relational**: Supports SQL queries and ACID transactions but also provides horizontal scaling and global distribution which traditional relational databases may struggle with.

4. **Performance**:
   - **High Performance**: Optimized for high throughput and low latency across large-scale, distributed systems.

5. **Management**:
   - **Fully Managed**: Handles infrastructure, backups, replication, and scaling automatically.

6. **Pricing**:
   - **Pricing Model**: Based on the number of nodes, storage usage, and network usage.

### **Google Cloud SQL**

**Overview**:
- **Type**: Fully managed relational database service that supports traditional SQL databases.
- **Primary Use Cases**: Smaller-scale applications, development, testing, and workloads that require traditional relational database features.

**Key Features**:
1. **Scalability**:
   - **Vertical Scaling**: Cloud SQL can scale vertically by upgrading instance types, but it does not support horizontal scaling like Cloud Spanner.
   - **Single Region**: Typically deployed in a single region, although replication to other regions is possible for high availability.

2. **Consistency and Availability**:
   - **ACID Compliance**: Supports ACID transactions but within a single region or limited replication setup.
   - **High Availability**: Offers automated backups, failover, and replication within a region, but not across multiple regions.

3. **Data Model**:
   - **Relational**: Supports MySQL, PostgreSQL, and SQL Server. Provides a familiar relational model with SQL query capabilities.

4. **Performance**:
   - **Good Performance**: Suitable for many applications, but performance may degrade if not scaled appropriately for very high workloads.

5. **Management**:
   - **Fully Managed**: Handles database administration tasks such as backups, patch management, and maintenance.

6. **Pricing**:
   - **Pricing Model**: Based on instance types, storage usage, and network usage. Generally more straightforward than Cloud Spanner’s pricing.

### **Comparison Summary**

| Feature                 | Google Cloud Spanner                | Google Cloud SQL                  |
|-------------------------|-------------------------------------|-----------------------------------|
| **Type**                | Globally distributed, horizontally scalable | Traditional, vertically scalable |
| **Data Model**          | Relational with global distribution | Relational (MySQL, PostgreSQL, SQL Server) |
| **Scalability**         | Horizontal scaling, global distribution | Vertical scaling, single-region |
| **Consistency**         | Strong consistency across regions   | ACID compliance within a region   |
| **Availability**        | High availability, disaster recovery | High availability within a region |
| **Management**          | Fully managed with automatic scaling | Fully managed with manual scaling |
| **Use Cases**           | Large-scale, mission-critical apps   | Smaller-scale, traditional apps   |
| **Pricing**             | Based on nodes, storage, network     | Based on instance types, storage, network |

**In summary**, **Google Cloud Spanner** is designed for large-scale, globally distributed applications requiring high availability and strong consistency. **Google Cloud SQL**, on the other hand, is suitable for applications needing traditional SQL databases with vertical scaling and regional deployment. The choice between the two depends on the specific needs for scalability, consistency, and database management.



---

### Question 22

Your financial services company is moving to cloud technology and wants to store 50 TB of financial time-series data in the cloud. This data is updated frequently and new data will be streaming in all the time. Your company also wants to move their existing Apache Hadoop jobs to the cloud to get insights into this data.

Which product should they use to store the data?
Cloud Bigtable
Google BigQuery
Google Cloud Storage
Google Cloud Datastore

From <https://www.passnexam.com/google/professional-data-engineer/3> 



Answer is Cloud Bigtable

Bigtable is GCP’s managed wide-column database. It is also a good option for migrat- ing on-premises Hadoop HBase databases to a managed database because Bigtable has an HBase interface.

Cloud Bigtable is a wide-column NoSQL database used for high-volume databases that require low millisecond (ms) latency. Cloud Bigtable is used for IoT, time-series, finance, and similar applications.

From <https://www.passnexam.com/google/professional-data-engineer/3> 

---
### Question 23

You are responsible for writing your company's ETL pipelines to run on an Apache Hadoop cluster. The pipeline will require some checkpointing and splitting pipelines. Which method should you use to write the pipelines?
- PigLatin using Pig
- HiveQL using Hive
- Java using MapReduce
- Python using MapReduce
