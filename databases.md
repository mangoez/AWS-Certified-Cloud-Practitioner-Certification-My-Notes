# Databases
## Key Value
* Dictionary like in Python
* Redis and Memcached puts data in the memory instead of the disk like other databases
  * Very fast
  * No round trip to disk
  * No queries, joins, but fast

Best for:
* **caching**
  * Pub/sub
  * Leaderboards
  * Not suitable for main database

Examples
* Etcd
* Redis
* Memcached


## Wide column
* Key value but instead with _row_ key and column values
* Unlike a relational database, has no schema
  * CQL - similar to SQL but more limited - no joins
* Easier to scale up and replicate data across multiple nodes
* Is decentralised
* Can scale horizontally

Best for:
* Time-series
* Historical records: netflix uses this for watch history
* High-write, low-read
* Not a primary database solution

Examples
* Apache Cassandra


## Document
* Documents contains key value pairs
* No schema
* Unstructured
* Documents are grouped together in collections
  * Collections can be indexed and organised
* Relational-ish queries
* No joins
* Instead of normalising data into small parts, embed data into single document
  * Reading is fast, but writing is more complex

Best for:
* Most apps
* Games
* IOT
* Unstructured data

Don't use for:
* Graphs
* Related data: social apps

Examples
* MongoDB
* Firestore
* DynamoDB
* CouchDB


## Relational
* SQL: structured query langauge
* Relational refers to the Relational Algebra that Edgar Codd created. That algebra provides operations like projection and join
* Relational allows tables to be related to one another
* Primary key refers to the id of a row in the table
* Foreign key refers to a foreign id that references a row in another table
* Organises data in the smallest normal form
* Requires a schema
* ACID compliant: When there is a transaction in the database, data validity is guaranteed even when there are hardware or network failures 
  * Atomicity
  * Consistency
  * Isolation
  * Durability
* Hard to scale, but some are designed to scale

Best for:
* Most apps

Don't use for:
* Unstructured data

Examples
* PostGres
* MySQL
* SQLServer


## Graph
![image](https://github.com/mangoez/AWS-Certified-Cloud-Practitioner-Certification-My-Notes/assets/69587452/3c5c9f41-8f74-4270-b0ef-f164daaea1ff)

* Treat the relationships as data as opposed to optionally creating that relationship as a table in the database
* Great alternative to SQL

Best for:
* Graphs!
* Knowledge graphs
* Recommendation engines

Examples:
* neo4j
* digraph


## Search
* Full text search engine
* Built on top of apache lucene
![image](https://github.com/mangoez/AWS-Certified-Cloud-Practitioner-Certification-My-Notes/assets/69587452/0d1d7f80-c264-4f87-b9fd-6b6142f56cd3)

* Can rank results with various algorithms
* Tokenizer is configurable to your needs
* From the documents, you get an inverted index which is essentially a hashmap where the key is the term and the Frequency and Document ID is the value

Best for:
* Search engines
* Typeahead

Examples:
* Elastic
* Meili


# SQL
* Foundation of Relational Databases
* Strict schema
* Tabular - rows and columns
* Primary key: id of the row in this table
* Attribute: value of the primary key
* Foreign key: id of the row in _another_ table
* Constraints: each column is allowed to be a certain datatype(s)
* Concentrated: tne node contains an entire copy of the data
* Vertical scaling: just get a better machine
* Horizontal scaling: more machines, but for SQL you have to make a master and hahve read replicas rather than split the data
* Relationships established via keys enforced by the system

# NoSQL
* Anything that is "non-relational"
  * The data is still relational, they just let go of some traditional constraints
  * This allows you to scale out easier
* Can be tabular, document, graph, etc
* Built to scale with high performance but queries comes at a cost
* Relies on Key Value, must know the key
* Storage hashes the input into a partition of physical storage
* Scaling just means adding more partitions!
* High throughput, low-latency reads and writes

## When to use SQL vs NoSQL
![image](https://github.com/mangoez/AWS-Certified-Cloud-Practitioner-Certification-My-Notes/assets/69587452/5f14e41a-e311-42fc-ae55-e50a6c1c82ab)

# Data categories
![image](https://github.com/mangoez/AWS-Certified-Cloud-Practitioner-Certification-My-Notes/assets/69587452/45cb3953-fa7b-4497-9db7-6803e70ef208)

# AWS databases
* Databases as a microservice not a monolith, data no longer in a single canonical store 
* Access pattern driven development and purpose built databases
![image](https://github.com/mangoez/AWS-Certified-Cloud-Practitioner-Certification-My-Notes/assets/69587452/fe74aed0-feed-432d-b57d-3cfb65fa730c)

## RDS
Managed relation database service with a choise of siz popular database engines
![image](https://github.com/mangoez/AWS-Certified-Cloud-Practitioner-Certification-My-Notes/assets/69587452/ed5ca534-814d-41a7-b341-9a1c6c99b7f6)

## Aurora
A cloud native relational database. MySQL and PostgreSQL compatible relational database built for cloud performance and availability of commercial grade databases. 
* Separated compute and storage layer
* The storage layer is giant, and shared between many compute nodes
![image](https://github.com/mangoez/AWS-Certified-Cloud-Practitioner-Certification-My-Notes/assets/69587452/4d4d561e-8c07-445a-a984-2f213e94e52a)
