# List of Tips
Extracted From System Design Interview by Alex Xu.

## System Design Interview

### When might be a right choice for a non-relational database
Non-relational databases might be the right choice if:
- Your application requires super-low latency.
- Your data are unstructured, or you do not have any relational data.
- You only need to serialize and deserialize data(JSON, XML, YAML, etc.).
- You need to store a massive amount of data.

### Vertical scaling vs horizontal scaling
When traffic is low, vertical scaling is a great option, and the simplicity of vertical scaling is its main advantage. Unfortunately, it comes with serious limitations:
- Vertical scaling has a hard limit. It is impossible to add unlimited CPU and memory to a single server.
- Vertical scaling does not have failover and redundancy. If one server goes down, the website/app goes down with it completely.

### Database replication
A master database generally only supports write operations. A slave database gets copies of the data from the master database and only supports read operations. All the data-modifying commands like insert, delete, or update must be sent to the master database.
Most applications require a much higher ratio of reads to write; thus, the number of slave databases in a system is usually larger than the number of master databases.

Advantages of database replication:
- `Better performance`: in the master-slave model, all writes and updates happen in master nodes; whereas, read operations are distributed across slave nodes. This model improves performance because it allows more queries to be processed in parallel.
- `Reliability`: If one of your database servers is destroyed by a natural disaster, such as a typhoon or an earthquake, data is still preserved. You do not need to worry about data loss because data is replicated across multiple locations.
- `High availability`: By replicating data across different locations, your website remains in operation even if a database is offline as you can access data stored in another database server.

### Considerations for using cache
Decide when to use cache. Consider using cache when data is read frequently but modified in frequently. Since cached data is stored in volatile memory, a cache server is not ideal for persisting data.
- `Expiration Policy`: It is a good practice to implement an expiration policy. Otherwise, the data will be stored in the memory permanently. It is advisable not to make the expiration date too short as this will cause the system to reload data from the database too frequently.
- `Consistency`: This involves keeping the data store and cache in sync. Inconsistency can happen because data-modifying operations on the data store and cache are not in the single transaction.
- `Eviction Policy`: Once the cache is full, any requests to add items to the cache might cause existing items to be removed. This is called cache eviction. Least-recently-used(LRU) is the most popular cache eviction policy. Other eviction policies, such as the Least Frequently Used(LFU) or First in First Out(FIFO), can be adopted to satisfy different use cases.

### Considerations of using a CDN
- `Setting an appropriate cache expiry`: For time-sensitive content, setting a cache expiry time is important. The cache expiry time should neither be too long nor too short. If it is too short, it can cause repeat reloading of content from origin servers to the CDN.
- `CDN fallback`: You should consider how your website/application copes with CDN failure. If there is a temporary CDN outage, clients should be able to detect the problem and request resources from the origin.

### Datacenters
To further scale our system, we need to decouple different components of the system so they can be scaled independently. Messaging queue is a key strategy employed by many real-world distributed systems to solve this problem.

## Scaling

### Vertical scaling
Vertical scaling comes with some serious drawbacks:
- You can add more CPU, RAM, etc. to your database server, but there are hardware limits. If you have a large user base, a single is not enough.
- Greater risk of single point of failures.
- The overall cost of vertical scaling is high. Powerful servers are much more expensive.

### Horizontal scaling
Horizontal scaling, as known as sharding, is the practice of adding more servers. Sharding separates large databases into smaller, more easily managed parts called `shards`. When choosing a sharding key, one of the most important criteria is to choose a key that can evenly distributed data.
Sharding is a great technique to scale the database, but it is far from a perfect solution. It introduces complexities and new challenges to the system:
- `Resharding data`: Resharding data is needed when:
  - A single shard could no longer hold more data due to rapid growth
  - Certain shards might experience shard exhaustion faster than others due to uneven data distribution.
- `Celebrity problem`: This is also called a hotspot key problem. Excessive access to a specific shard could cause server overload.
- `Join and de-normalization`: Once a database has been sharded across multiple servers, it is hard to perform join operations across database shards. A common workaround is to de-normalize the database so that queries can be performed in a single table.

## Latency
- Memory is fast, but the disk is slow.
- Avoid disk seeks if possible.
- Simple compression algorithms are fast.
- Compress data before sending it over the internet if possible.
- Data centers are usually in different regions, and it takes time to send data between them.

## Questions
- The ability to ask good questions is also an essential skill, and many interviewers specifically look for this skill.
- In system design interview, giving out an answer quickly without thinking gives you no bonus points. Answering without a thorough understanding of the requirements is a huge red flag as the interview is not a trivia contest. There is no right answer.

### What questions to ask?
Ask questions to understand the exact requirements. Here is a list of questions to help you get started:
- What specific features are we going to build?
- How many users does the product have?
- How fast does the company anticipate to scale up? What are the anticipated scales in 3 months, 6 months, and a year?
- What is the company's technology stack? What existing services you might leverage to simplify the design?

## High-level architecture

### Rate limit
The basic idea of rate limiting algorithms is simple. At the high-level, we need a counter to keep track of how many requests are sent from the same user, IP, address, etc. If the counter is larger than the limit, the request is disallowed.
Where shall we store counters? Using the database is not a good idea due to slowness of disk access. In-memory cache is chosen because it is fast and supports time-based expiration strategy. For instance, Redis is a popular option to implement rate limiting.