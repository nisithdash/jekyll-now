---
published: true
---



“ _Distributed transactions are icebergs: they can be hard to see, and they can sink your ship_ ” - Graham Lea

![saga_confirm.png]({{site.baseurl}}/_posts/saga_confirm.png)

Transactions are fundamental to any software system in order to maintain consistency of data when it is being concurrently read and modified by multiple processes within such a system. We are all well aware of ACID transactional semantics that provides guarantees that each thread or process has exclusive access to the data during it’s interaction. Transactions work fine to enforce those guarantees when we have a monolithic application directly accessing a single transactional data source. However, in cases where we need to interact with multiple transactional data sources to complete an atomic unit of work, we need to employ the de facto standard of XA that uses two-phase commit to ensure all participants in the transaction either commit or rollback. Distributed transactions poses a host of problems even when a small number of participants are involved in a local transaction. It minimizes system throughput, severely limits our ability to scaling out transactional resources. Again, with increasing concurrency, the risk of contentions within the system becomes high and to an extent where performance is simply unacceptable.


Most modern systems are extremely distributed in nature and are usually composed of multiple geographically dispersed resources like databases, NoSQL data stores, messaging queues, application caches etc. They need to be designed with support for extremely high levels of scalability and availability.  They need to be resilient to infrastructure and network failures. They need to be able to quickly recover from partial failures due to temporary unavailability of one or more resources. They need to frequently interact with non-transactional resources like NoSQL databases such as MongoDB and Cassandra or message brokers like RabbitMQ or Apache Kafka. All of these reasons make it impossible to use distributed transaction protocols like XA to maintain strict data consistency. As a matter of fact, eventual consistency of data is a widely accepted compromise to achieve a extremely high degree of scalability and availability. 

In this blog post, I will provide an introduction of Saga, a completely new approach to doing transactions correctly in a highly distributed, highly scalable modern system without encountering any of the drawbacks mentioned earlier.
