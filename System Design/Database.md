# Database # 
## SQL VS NoSQL

|             |         SQL    |       NoSQL |
| ----------- | ----------- | ----------- |
| Header      | Structured and have predefined schemas       | Unstructured, distributed and dynamic schemas       |
| Storage   | Rows and columns        | Key-value stores - Redis, Dynamo <br /> Document DB - MongoDB <br /> Columnar DB - Cassandra <br /> Graph DB - Neo4j        |
| Querying    | Use SQL (structured query language) for defining and manipulating the data | Queries are focused on a collection of documents        |
| Scalability    | Most are vertically scalable        | Horizontally scalable        |
| ACID    | Mostly       |   Most sacrifice ACID for performance and scalability  |
| Example   | Phone book that stores phone numbers and addresses        | File folders  that hold everything from a person’s address and phone number to their Facebook ‘likes’ and online shopping preferences.       |


When to choose SQL, DocumentDB, GraphDB, ColumnarDB?

- _SQL_
	- Structured data 
	- Need to ensure ACID compliance.
	- Data is structured and unchanging

- _DocumentDB_
	- Lots of data in terms of structure (data types)
	- Complex queries
- _ColumnarDB_
	- Ever increasing data 
	- Finite queries

## CAP Theorem
The theorem states that it is impossible to get more than two of the following guarantees in distributed system.

- _C - Consistency_ 

	All nodes sees the same data at the same time. Consistency is
achieved by updating several nodes before allowing further reads

- _A - Availability_

	Every request gets a response on success/failure. Availability is
achieved by replicating the data across different servers.

- _P - Partition Tolerance_ 

	The system continues to work despite message loss or
partial failure. Data is sufficiently replicated across combinations of nodes and networks to keep the system up through intermittent outages

	<ins><b>CP Database</b></ins>

	Delivers consistency and partition tolerance at the expense of availability. Ex. <b>MongoDB</b>

	<ins><b>AP Database</b></ins>
	
	Delivers availability and partition tolerance at the expense of consistency. Ex. <b>CassandraDB</b>

	<ins><b>CA Database</b></ins>
	
	Delivers consistency and availability at the expense of partition tolerance. In a distributed system, partitions can’t be avoided. So, while we can discuss a CA distributed database in theory, for all practical purposes, a CA distributed database can’t exist. However, this doesn’t mean you can’t have a CA database for your distributed application if you need one. Many relational databases, such as PostgreSQL, deliver consistency and availability and can be deployed to multiple nodes using replication. 


## Redundancy/ Replication

- Redundancy

	Redundancy is the duplication of critical components or functions of a system with the intention of increasing the reliability of the system, usually in the form of a backup or fail-safe, or to improve actual system performance.

- Replication

	Sharing information to ensure consistency between redundant resources, such as software or hardware components, to improve reliability, fault-tolerance, or accessibility. The master gets all the updates, which then ripple through to the slaves.

## Indexes 
The goal of creating an index on a particular table in a database is to make it faster to search through the table and find the row or rows that we want.
Indexes can be created using one or more columns of a database table,
providing the basis for both rapid random lookups and efficient access of
ordered records.

An index can dramatically speed up data retrieval but may itself <b> be large due to the additional keys, which slow down data insertion & update.</b> When adding rows or making updates to existing rows for a table with an
active index, we not only have to write the data but also have to update the
index. This will decrease the write performance. This performance
degradation applies to all insert, update, and delete operations for the table.

For this reason, adding unnecessary indexes on tables should be avoided and
indexes that are no longer used should be removed.


## Sharding/ Partitioning

- Horizontal partitioning

	Put different rows into different tables. The key problem with this approach is that if the value whose range is used for sharding isn’t chosen carefully, then the partitioning scheme will lead to unbalanced servers

- Vertical Partitioning

	Divide our data to store tables related to a specific feature in their own server. The main problem with this approach is that if our application
experiences additional growth, then it may be necessary to further partition a feature specific DB across various servers. 

### Partitioning criteria

- Hash-based partitioning

	Apply a hash function to some key attributes of the entity we are storing.

- List partitioning

	Each partition is assigned a list of values, so whenever we want to insert a new record, we will see which partition contains our key and then store it there

- Round-robin partitioning

	This is a very simple strategy that ensures uniform data distribution. With ‘n’ partitions, the ‘i’ tuple is assigned to partition (i mod n).

- Composite partitioning

	Under this scheme, we combine any of the above partitioning schemes to devise a new scheme. For example, first applying a list partitioning scheme and then a hash based partitioning.


### Partitioning problems

- Joins and Denormalization
- Referential integrity
- Rebalancing


References: 

https://www.ibm.com/cloud/learn/cap-theorem

https://www.youtube.com/watch?v=cODCpXtPHbQ&ab_channel=codeKarle


