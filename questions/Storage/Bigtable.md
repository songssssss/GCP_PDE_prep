

Question 22

Your financial services company is moving to cloud technology and wants to store 50 TB of financial time-series data in the cloud. This data is updated frequently and new data will be streaming in all the time. Your company also wants to move their existing Apache Hadoop jobs to the cloud to get insights into this data.

Which product should they use to store the data?

Cloud Bigtable
Google BigQuery
Google Cloud Storage
Google Cloud Datastore


Bigtable
Refer to this link for doc.

A managed service.
No transactional support (so can handle petabytes of data)
Bigtable is a key/value store, not a relational store.
It does not support joins, and transactions are supported only within a single row.
HBase and Cassandra are similar wide-column databases.
Supports HBase API
Bigtable tables are sparse. A column doesn't take up any space in a row that doesn't use the column
When you create a Cloud Bigtable instance and cluster, your choice of SSD or HDD storage for the cluster is permanent. If you need to convert an existing HDD cluster to SSD, or vice-versa, you can export the data from the existing instance and import the data into a new instance.
Data Replication: Replications is copying data across multiple regions to increase durability. Just add another cluster and it will be possible to replicate the data.
No downtime for cluster resize.
While instance creation, clusters can be configured on number of nodes, SSD or HDD, Regional or Zone etc.
Scales linearly. Increasing no. of nodes increases performance.
Mutations or Deletions takes extra storage as mutations are stored sequentially.
Deletions are just specialized mutations.
Automatic read-write operations to reorganize the data or to remove deleted items.
A Cloud Bigtable instance is mostly just a container for your clusters and nodes, which do all of the real work.
Tables belong to instances, not to clusters or nodes. So if you have an instance with up to 2 clusters, you can't assign tables to individual clusters
For time-series data, financial data or IOT data, BigTable is recommended as it is highly scalable.
Backups are also supported.
It does not support SQL queries, joins or multi-row transactions.
Not good for data less than 1TB of data or items greater than 10MB.
cbt is a tool for doing basic interactions with Cloud Bigtable
Garbage collection is supported.
Supports max of 1,000 tables in each instance.
Can use up to around 100 column families.
Empty columns don’t take up any space. Can create large number of columns, even if most columns are empty in most rows
Adding more nodes to a cluster (not replication) can improve the write performance
Google recommends adding nodes when storage utilization is > 70%
BigTable provides lowest latency
Multi-cluster routing is beneficial in cases where high availability is needed
Field promotion avoids hotspotting
It is recommended to create your Compute Engine instance in the same zone as your Cloud Bigtable instance for the best possible performance. If it's not possible to create a instance in the same zone, you should create your instance in another zone within the same region
The only way to achieve strong consistency in Cloud Bigtable is by having all reads routed from a single cluster and using the other replicas only for failover
Security : Can manage security at project, instance and table levels and it can be managed via IAM. For example, you can grant the ability to: Read from, but not write to, any table within the project. Read from and write to any table within the project, but not manage instances. Read from and write to any table within the project, and manage instances


DataStore
NoSQL DB, serverless, highly scalable
AutoScale supported.
High availability of reads and writes.
Fully managed with no planned downtime
It is a fully managed and serverless solution that allows for transactions and will autoscale (storage and compute) without the need to manage any infrastructure
Each transaction is guaranteed to be atomic, meaning that transactions are never partially applied. Either all of the operations in the transaction are applied, or none of them are applied.
Document kind storage
Tightly coupled with app engine, so one project can have just one firestore/datastore
GQL (Google Query Language) is used which is similar to SQL
Support ACID (Atomicity, Consistency, Isolation, Durability) transactions
Replication across different regions is possible
Export is only available with gcloud utility only.
Data exported from one Datastore mode database can be imported into another Datastore mode database, even one in another project
Cloud Datastore only retrieves results using indexes, it does not scan entities checking filter conditions.
Comparison b/w DataStore and RDBMS
DataStore	RDBMS
Kind	Table
Key	PK
Entity	Row
Property	Column
