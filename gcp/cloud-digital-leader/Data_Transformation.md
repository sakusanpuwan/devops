# GCP Data Transformation
## Value of Data
Data is defined as a collection of facts, such as numbers, words, measurements, observations or even just descriptions of things. Data is the raw material that we use to create information and knowledge. It can be structured (like in databases) or unstructured (like text or images). 

Data is essential for driving innovation and differentiation and is key to unlocking value from AI. Data powers AI-driven business   insights, support decision-making, and drive how companies build and run their applications. When data is collected, processed, and analyzed effectively, it can reveal patterns, trends, and relationships that can help organizations make informed decisions, improve operations, and create new products or services.

Data can be categorized into different types, such as:
- **Structured Data**: This type of data is organized in a predefined manner, often in rows and columns, making it easy to search and analyze. Examples include databases, spreadsheets, and CSV files.
- **Unstructured Data**: This type of data does not have a predefined format and can be more difficult to analyze. Examples include text documents, images, videos, and social media posts.
- **Semi-Structured Data**: This type of data has some organizational properties but does not fit into a rigid structure like structured data. Examples include JSON, XML, and HTML files.

Data can be stored and managed in different ways, such as:
- **Databases**: Structured organised collection of data stored in relational databases (like MySQL, PostgreSQL) or NoSQL databases (like MongoDB, Cassandra). 
  - Relational Databases: These databases store data in tables with predefined relationships between them by joining tables. They use SQL (Structured Query Language) for querying and managing data. Examples include MySQL, PostgreSQL, and Microsoft SQL Server.
  - Non Relational Databases: These databases are flexible to handle unstructured or semi-structured data and do not require a fixed schema. They can be document-based, key-value, column-family, or graph databases. Examples include MongoDB (document-based), Redis (key-value), Cassandra (column-family), and Neo4j (graph).
- **Data Lakes**: A vast storage repository that holds raw data in its original format, ready for any type of analysis. Examples include Amazon S3, Azure Data Lake Storage, and Google Cloud Storage.
- **Data Warehouses**: Centralised system that consolidates data from multiple sources and is designed for fast querying, analytical processing and reporting. Examples include Amazon Redshift, Azure Synapse Analytics, and Google BigQuery.

**First-party Data** is the proprietary customer datasets that a business collects from customer or audience transactions and interactions. These datasets might include information about digital interactions, like the length of time a user spends on a web page.

**Second-party data** often describes first-party data from another organization, such as a partner or other business in their supply chain, that can be easily deployed to augment a company's internal datasets.

**Third-party data** are datasets collected and managed by organizations that don’t directly interact with an organization's customers or business. These datasets might come from government, nonprofit, or academic sources, like weather or public demographic data, or from industry-specific sources like analyst reports or industry benchmarking.

### Data Value Chain
- Data Generation - data is generated from various sources, such as sensors, social media, transactions, and more.
- Data Collection - raw data is extracted from various sources, such as sensors, social media, transactions, and more.
- Data Processing - collected data is processed and transformed into a usable format.
- Data Storing - processed data is stored in a data warehouse, data lake, or other storage solution.
- Data Analysis - processed data is analyzed to extract insights and patterns.
- Data Activation - analyzed data is used to drive decision-making and business outcomes.

### Data Governance 
Means setting internal standards or data policies that apply to how data is gathered, stored, processed, and disposed of. It also governs who can access certain data and what data is under governance. 

- Valuable:  implements processes to ensure high quality data, and provides a platform that makes it easier to share data securely with stakeholders across the organization.
- Decision-Making:  provides a framework for making informed decisions about data management and usage, ensuring that data is used effectively to drive business outcomes.
- Improves cost control -  helps organizations manage resources and operate more effectively by eliminating data duplication caused by information silos
- Enhances regulatory compliance -  helps organizations comply with data protection regulations by implementing policies and procedures for data handling and security.
- Increases trust and transparency -  promotes trust and transparency by ensuring that data is accurate
- Reduces risk -  helps organizations identify and mitigate risks associated with data management, such as data breaches or loss of data integrity.

## Data Management Solutions
### Unstructured Data Storage
- Cloud Storage: Offers object storage (computer data storage architecture that manages data as objects instead of files with folder hierarchy). Objects are stored in packaged format that contain the binary form of the actual data, metadata(date, author, type) and a global unique identifier (URL). Object storage is ideal for web tech as it can store videos, pictures and audio. Unstrucutured as it doesn't have a predefined data model like database format. 
  - Standard Storage: Frequently accessed or hot data / data that's stored for only brief periods of time.
  - Nearline Storage: Infrequently accessed data like reading or modifying data once a month or less. E.g. data backup, archiving
  - Coldline Storage: Low cost storage for infrequently accessed data. Meant for reading or modifying data at most once every 90 days
  - Archive Storage: Lowest cost option, used for data archiving, online backup and disaster recovery. Meant for data that is accessed less than once a year
  - All options offer unlimited storage with no minmum object size requirements, worldwide access and locations, low latency and high durability. Autoclass which automatically transitions objects to appropriate storage class based on access patterns.

### Structured Data Storage
Structured data consists of numbers and values that are organized in a predefined format in a relational database. It is typically stored in tables with rows and columns, making it easy to search and analyze using SQL (Structured Query Language). Examples of structured data include customer information, sales data, and inventory data.

- Cloud SQL: Fully managed relational database service that supports MySQL, PostgreSQL and SQL Server. It offers high availability (99.95%), automatic backups, and seamless integration with other GCP services. It is ideal for applications that require a local relational database with minimal management overhead.
  
- Spanner: Globally distributed, horizontally unlimited scalable, strongly consistent relational database service. It is designed for mission-critical applications that require high availability (99.999%) and low latency at global scale. Spanner offers features like synchronous replication, automatic sharding, and support for SQL queries.

- BigQuery: Serverless, highly scalable data warehouse service that enables fast SQL queries over large datasets. Provides storage and analytics. Encrypted at rest by default. Also has built in ML features for data analysis. It is ideal for analyzing large datasets and performing complex queries with high performance.

### Semi-structured Data Storage
Semi-structured data contains elements of both structured and unstructured data. It does have some defining and consistency but doesn't follow a rigid structure like a relation database. Easy to organise as it usually contains some organisational properties such as tags or metadata. E.g email message. Actual content of email is unstructured but it has metadata such as sender, recipient, subject and timestamp which is structured.

- Firestore: a flexible, horizontally auto scalable, NoSQL cloud database for storing and syncing data in real-time. Firestore performs data storage in the form of documents, with the documents being stored in collections. Also provides offline usage through a comprehensive database on users’ devices.
- Bigtable: Fully managed NoSQL database service for large analytical and operational workloads. It's the same database that powers many core Google services, including Search, Analytics, Maps, and Gmail. Bigtable is designed to handle large workloads at consistent low latency, which means Bigtable responds to requests quickly, and high throughput, which means it can send and receive large amounts of data. A good choice for both operational and analytical applications, including Internet of Things, user analytics, and financial data analysis. A good option if you're working with more than 1 terabyte of data with high throughput. 

---
Online Transaction Processing (OLTP) used when fast data inserts and updates are required to build row based records. 

Online Analytical Processing (OLAP) used when entire datasets need to be read. 

### GCP Data Service Selection Guide

| Requirement | Best GCP Service | Why it fits |
|---|---|---|
| Transactional data + SQL queries | Cloud SQL or Spanner | Cloud SQL is ideal for local to regional scale; Spanner is best for global scale and high availability. |
| Transactional data + NoSQL access | Firestore | A flexible NoSQL database for real-time apps, syncing, and scalable document storage. |
| Analytical workloads + SQL queries | BigQuery | A serverless data warehouse optimized for fast SQL analytics on large datasets. |
| Analytical workloads + non-SQL access | Bigtable | A high-throughput NoSQL database designed for large-scale analytical and operational workloads. |

---
Running modern apps on legacy, on-premises databases requires overcoming expensive, time-consuming challenges around latency, throughput, availability and scaling. 

With database modernisation, orgs can migrate data from trad databases to fully managed modern databases with relative ease.
- Lift and Shift: Rehost your database to the cloud with minimal changes. This is the quickest way to migrate, but may not take full advantage of cloud capabilities. Google Cloud's Database Migration Service (DMS) can help with this process.

Datastream is the Google Cloud product which can be used to synchronize data across databases, storage systems, and applications

Database Migration Service (DMS) is a fully managed service that can migrate your production database to Cloud SQL with minimal downtime. 

## Making Data Useful and Accessible
### Business Intelligence
Looker is Google Cloud's business intelligence platform that helps individuals and teams analyse, visualise and share data. This includes creating interactive dashboards, reports. Looker supports BigQuery, along with 60 different SQL databases. It's also 100% web based making it easy to integrate into existing workflows and share insights across multiple teams. 

### Streaming Analytics
Batch processing often processes large volumes of data with long periods of latency. 

Streaming analytics is the processing and analysing of data records continously instead of in batches. This is useful for types of data sources that send data in small sizes in a continous flow as the data is generated. E.g. equipment sensors, clickstreams, social media feeds, stock market data. They can analyse data in real time and provide insights such as metering, server activity, geolocation, website clicks.

Google Cloud offers two main streaming analytics to ingest, process and analyse event streams in real time:
- Pub/Sub: A message service which ingests hundred of millions of events per second from various device streams. Short for Publisher/Subscriber or publish messages to subscribers. 
- Dataflow creates a pipeline to process both streaming data and batch data. This process is the extract, transform and load (ETL) process. It's open source and is built on Google's infrastructure (e.g. integrates with BigQuery). Allows for reliable auto scaling to meet data pipeline demands. It's serverless and fully managed meaning devs can build and run apps without having to provision or managed back-end infrastructure. 