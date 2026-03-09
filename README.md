# SystemDesign



[API Architecture](https://github.com/abhishek-gupta-108/SystemDesign/blob/main/APIArchitecture.md)

## General
1. [Capacity Estimation](https://github.com/abhishek-gupta-108/SystemDesign/blob/main/Estimation.md)
2. [API Architecture - Rest, gRPC, Websockets, WebHooks](https://github.com/abhishek-gupta-108/SystemDesign/blob/main/APIArchitecture.md)
3. API Gateway
4. Proxy and Reverse Proxy
5. Load Balancers
6. 

## DATABASES

1. [Why DB Partitioning](https://github.com/abhishek-gupta-108/SystemDesign/blob/main/Db_Partition.md)
2. [Write Ahead Logging](https://www.dropbox.com/scl/fi/yhzvs7dk3oxym3lnm8dtk/WriteAheadLogging.docx?cloud_editor=word&dl=0&rlkey=mz7ym3nxzha8vd8sxjzgll0fp)


## SQL
1. Transactions
2. ACID property
3. Indexing
4. Normalization
5. Denormalization

As an Engineer you should know the following concepts
1. Indexation
2. WAL
3. CDC ( Change Description Capture)
4. SQL vs NoSQL -

## Case Studies
1. [Fb Like](https://github.com/abhishek-gupta-108/SystemDesign/blob/main/Case%20Studies/Social%20Media%20Post.md)


## Message Queues
1. Apache Kafka
2. RabbitMQ
3. ActiveMQ

## Architecture
1. Event Driven Architecture
2. CRQS
3. Saga

## To Learn
1. Idempotency → Prevents duplicate payments
2. Pagination → Keeps your DB from dying
3. Versioning → Lets you evolve APIs without breaking clients
4. Rate limiting → Protects your service from abuse
5. Error codes → Helps clients handle failures correctly
6. Caching → Reduces load by 90%
7. JWT security → Prevents leaking sensitive data
8. N+1 queries → The difference between 10ms and 10s response time
9. Docs → Stops the `how does this API work?` Slack messages
10. Consistency → Choose the right tradeoff for your use case
11. Observability → You can’t fix what you can’t see.
12. Logs, metrics, traces save more production incidents than code.

1. Load Balancing
2. SQL vs NoSQL
3. Idempotency
4. Message Queues
5. CAP Theorem
6. APIs
7. Batch vs Stream Processing
8. Caching Strategies
9. Webhooks
10. Availability
11. Data Sharding and Partitioning
12. Bloom Filters
13. Stateful vs Stateless Architecture
14. Algorithms in Distributed Systems
15. API Gateways
16. Proxy vs Reverse Proxy
17. Sharding
18. Long Polling vs WebSockets
19. Consistent Hashing
20. gRPC, tRPC, GraphQL, or REST
21. Caching
22. Scaling
23. Cache Eviction Policies
24. Databases in System Design
25. JWTs
26. Services in System Design
27. Concurrency vs Parallelism
28. CDC
29. ACID Transactions
30. CDN
31. Sync vs Async
32. Rate Limiting Algorithms
33. REST
34. gRPC vs REST tradeoffs
35. Fault Tolerance


## Back to the topics: 
1. Networking basics
 ↣ IP addressing
 ↣ Domain Name System (DNS)
 ↣ Client server model
 ↣ HTTP request response lifecycle
 ↣ TLS and HTTPS

2. Transport and streaming
 ↣ TCP
 ↣ UDP
 ↣ WebSockets
 ↣ HTTP/2 and HTTP/3
 ↣ Long polling and Server Sent Events

3. Cloud and infrastructure
 ↣ Cloud computing models (IaaS, PaaS, SaaS)
 ↣ Regions and availability zones
 ↣ Virtual machines and containers
 ↣ Kubernetes and orchestration basics
 ↣ Service discovery

4. Traffic management layer
 ↣ Load balancers (L4 and L7)
 ↣ Forward proxy
 ↣ Reverse proxy
 ↣ API gateway
 ↣ Rate limiting

5. Data storage fundamentals
 ↣ Relational databases
 ↣ NoSQL families (key value, document, column, graph)
 ↣ SQL vs NoSQL trade offs
 ↣ Indexing strategies
 ↣ Transactions and isolation levels

6. Distributed data patterns
 ↣ Replication
 ↣ Sharding and partitioning
 ↣ Consistency models (strong, eventual)
 ↣ Leader follower architecture
 ↣ CAP theorem

7. Caching and performance
 ↣ Cache basics, hits and misses
 ↣ Cache eviction policies
 ↣ Cache aside pattern
 ↣ Read through and write through
 ↣ Content Delivery Network (CDN)

8. Messaging and async workflows
 ↣ Message queues
 ↣ Publish subscribe
 ↣ Event driven architecture
 ↣ Idempotency
 ↣ Delivery semantics (at least once, at most once, exactly once)

9. Storage and media handling
 ↣ Object storage
 ↣ Block vs file storage
 ↣ Data compression
 ↣ Encoding and transcoding
 ↣ Tiered storage and lifecycle policies

10. Reliability and observability
 ↣ High availability and nines
 ↣ Fault tolerance and redundancy
 ↣ Health checks and circuit breakers
 ↣ Logging and log aggregation
 ↣ Metrics, monitoring and alerting



Apache kafka vs RabbitMq



## Case Studies:

1. How OTTs like Hotstar, Netflix implement Live Steaming? _ Like Cricket match, Boxing Match?
2. How infinite scroll works
3. How Whatsapp Stores/created chat?
4. Tinder - User DB Sharding by location

## Bottlenecks

