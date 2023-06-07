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