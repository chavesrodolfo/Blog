---
title: 'SQL vs NoSQL'
excerpt: 'Decide what kind of database we should use in each situation is a hard decision sometimes. The reason of this aticle is to turn this decision easier and also to be a material for consultation in the future.'
coverImage: '/assets/blog/sql-vs-nosql/sql-vs-nosql.jpg'
date: '2020-10-22'
author:
  name: Rodolfo Chaves Fernandes
  picture: '/assets/blog/authors/rodolfo.png'
ogImage:
  url: '/assets/blog/sql-vs-nosql/sql-vs-nosql.jpg'
---

Hey Folks!

Decide what kind of database we should use in each situation is a hard decision sometimes. The reason of this aticle is to turn this decision easier and also to be a material for consultation in the future.

Comparative
---

| SQL | NoSQL |
| :--- | :--- |
| Pre-defined schema | Dynamic schema and not structured data |
| Table oriented | Based on document, graph, table or key/value |
| Table has a unique pre-defined structure | Each document has it's own structure |
| Impossible to create new fields without affect all structure | It's possible to create nem fields without break |
| Mostly verticaly scalable | Horizontaly scalable |
| Performance is affected manipulation and consulting large data volumes | High performance for large data volumes |
| ACID compliance (Atomicity, Consistency, Isolation, Durability) | No ACID |

> Overall, the decision of using SQL or NoSQL requires some comparison contrast to determine which database best fits the solution needs.

*Use cases:*

**SQL**
* MySQL
* Oracle
* PostgreSQL
* Microsoft SQL Server
* Db2

**NoSQL**
* MongoDB
* BigTable
* Redis
* RavenDB
* Cassandra
* HBase
* Neo4j
* CouchDB
* DynamoDB