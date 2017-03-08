# **FAQ** <a name="top"></a>
- [What is TimescaleDB?](#what)
- [Why build another time-series database?](#why-build)
- [Why should I use TimescaleDB?](#why-use)
- [Do you really support “all of SQL”](#sql-support)
- [How far can TimescaleDB scale?](#scaling)
- [Why would I use TimescaleDB over vanilla PostgreSQL?](#vs-postgres)
- [How compatible is TimescaleDB with PostgreSQL?](#postgres compatibility)
- [What can I use TimescaleDB for?](#what-for)
- [When is TimescaleDB a good choice?](#when-good)
- [When is TimescaleDB not a good choice?](#when-less-good)
- [What is the TimescaleDB open-source license?](#license)
- [Can I get support or a commercial license?](#license-commercial)
- [Where can I get TimescaleDB source code?](#where)

### **What is TimescaleDB?** <a name="what"></a>
  TimescaleDB is an open source time-series database engineered up from PostgreSQL, optimized for fast ingest and complex queries. Unlike traditional RDBMS, TimescaleDB transparently scales-out horizontally across multiple servers; unlike NoSQL databases, TimescaleDB natively supports all of SQL. TimescaleDB is distributed under the Apache 2.0 license. [[Top]](#top)

### **Why build another time-series database?** <a name="why-build"></a>
  Time-series data is cropping up in more and more places: monitoring and DevOps, sensor data and IoT, financial data, logistics data, app usage data, and more. Often this data is high in volume and complex in nature (e.g., multiple measurements and labels associated with a single time). This means that storing time-series data demands both scale and efficient complex queries. Yet achieving both of these properties has remained elusive. Users have typically been faced with the trade-off between the horizontally scalability of NoSQL vs. the query power of relational databases. We needed something that offered both, so we built it. [[Top]](#top)

### **Why should I use TimescaleDB?** <a name="why-use"></a>
  As time becomes a more critical dimension along which data is measured, TimescaleDB enables developers and organizations to harness more of its power: analyzing the past, understanding the present, and predicting the future. Unifying time-series data and relational data at the query level removes data silos, and makes demos and prototypes easier to get off the ground. The combination of scalability and a full SQL interface empowers a broad variety of people across an organization (e.g., developers, product managers, business analysts, etc.) to directly ask questions of the data. In other words, by supporting a query language already in wide use, TimescaleDB ensures that your questions are limited by your imagination, not the database. [[Top]](#top)

### **Do you really support “all of SQL”?** <a name="sql-support"></a>
  Yes, all of SQL, including: secondary indices, JOINs, window functions. In fact, to the outside world, TimescaleDB looks like a PostgreSQL database: You connect to the database as if it’s PostgreSQL, and you can administer the database as if it’s PostgreSQL. Any tools and libraries that connect with PostgreSQL will automatically work with TimescaleDB. [[Top]](#top)

### **How far can TimescaleDB scale?** <a name="scaling"></a>
  TimescaleDB scales out horizontally in a linear fashion across many servers. All servers can receive and process queries, and store data; TimescaleDB does not use any specialized primary server or transaction coordination. It is designed to combine the scalability of popular NoSQL databases, with the native query complexity supported by RDBMS systems. [[Top]](#top)

### **Why would I use TimescaleDB over vanilla PostgreSQL?** <a name="vs-postgres"></a>
  * Scale, performance, and features. While vanilla PostgreSQL is suitable for time-series data at low volumes, it does not scale well to the volume of data that most time-series applications produce, especially when running on a single server. TimescaleDB performs better for time-series single-node deployments, and allows scaling out in ways that Vanilla PostgreSQL does not support.
  * In particular, vanilla PostgreSQL has poor write performance for large tables, and this problem only becomes worse over time as data volume grows linearly in time. These problems emerge when table indexes can no longer fit in memory, as each insert will translate to many disk fetches to swap in portions of the indexes’ B-Trees. Further, any data deletion (to save space or to implement data retention policies) will require expensive “vacuuming” operations to defragment the disk storage associated with such tables.
  * TimescaleDB also includes time-series specific features not included in vanilla PostgreSQL (e.g., [data retention](https://github.com/timescaledb/timescaledb/blob/master/docs/API.md)), with more to come.
  [[Top]](#top)

### **How compatible is TimescaleDB with PostgreSQL?** <a name="postgres-compatibility"></a>
  TimescaleDB is implemented as an extension to PostgreSQL that introduces transparent scalability and performance optimizations, as well as time-series specific features (e.g., data retention policies). TimescaleDB connects with any and all third party tools that communicate with standard PostgreSQL connectors. Migrating from Vanilla PostgreSQL to TimescaleDB is one line of SQL code (i.e., a COPY command); you can continue to run your existing databases. [[Top]](#top)

### **What can I use TimescaleDB for?** <a name="what-for"></a>
  TimescaleDB can be used to store large amounts of time-series data, perform complex ad-hoc queries in performant ways, monitor the performance of applications, models and devices, power a number of visualization tools, run predictive models, empower more of your organization to gain access and insights from your data, and unsilo your data stores. [[Top]](#top)

### **When is TimescaleDB a good choice?**  <a name="when-good"></a>
TimescaleDB is a good choice if:

  * You collect and want to analyze time-series data using SQL.
  * Your queries can be complex in nature, but also need to be performant.
  * You index many metrics and don’t want to be limited in the complexity of the analysis of that data.
  * You want to free up development time for your engineers.
  * You want to empower more of your organization to access more of your time-series data and your business / relational data.
  * You don’t want to have to optimize your storage architecture around a rigid set of query patterns, as you know your data will ultimately be much more valuable (and to more of your organization) than this one use case.
  * You need to actively monitor your apps or devices and want a broader selection of visualization power and tools.
  * You need to perform more complex ad hoc analyses of your time-series data along with your relational / business data (i.e. JOINS).
  * You already use and like PostgreSQL, and don’t want to have to “give it up” to scale to larger volumes of data.
  * You had to abandon your PostgreSQL or other RDBMS system for a Hadoop/NoSQL system due to scaling concerns or issues, and that trade-off makes you sad. [[Top]](#top)

### **When is TimescaleDB not a good choice?**  <a name="when-less-good"></a>
TimescaleDB would not be a good choice if you have:

  * Simple-read requirements: When most of your query patterns are simple in nature (e.g., key-based lookups, or one dimensional rollups over time).
  * Low available storage: When resource constraints place storage at a premium, and heavy compression is required. (Although this is an area of active development, and we expect TimescaleDB to improve.)
  * Sparse and/or unstructured data: When your time-series data is especially sparse and/or generally unstructured. (But even if your data is partially structured, TimescaleDB includes a JSONB field type for the unstructured part(s). This allows you to maintain indexes on the structured parts of your data while retaining the flexibility of unstructured storage.) [[Top]](#top)

### **What is the TimescaleDB open-source license?** <a name="license"></a>
  Apache 2.0 [[Top]](#top)
### **Can I get support or a commercial license?** <a name="license-commercial"></a>
  Yes. Please contact us for more information. [[Top]](#top)
### **Where can I get TimescaleDB source code?** <a name="where"></a>
  See our GitHub repo at https://github.com/timescaledb/timescaledb

[[Top]](#top)