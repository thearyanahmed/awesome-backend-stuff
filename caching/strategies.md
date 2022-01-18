# Caching Strategies

### Lazy Loading

   *Lazy loading* is a caching strategy that loads data into the cache only when necessary. Basically when a client requests for data and if the cache is empty or expired its TTL, it is fetched and cached.

   *Pros*

   1. Only requested data is cached. So cache doesn’t take space for unnecessary stuff.
   2. Application will continue to work even with a node failure. It will increase latency/ decrease performance cause every request on the node is going to call the data store.

   *Cons*

   1. Each cache miss has a penalty.
      1. Initial request for data in the cache ( as it doesn’t exist in the cache, it’s an useless (somewhat) request )
      2. Query the database
      3. Write to cache
   2. Stale data. If data is only written to cache when there is a cache miss, it will probably produce stale data. A way to solve is to follow write through strategy or TTL.

### Write through

   Write through is a strategy is when data is written to database, it is also written to the cache.

   *Pros*

   1. Data is never stale.

   *Cons*

   1. Every write request has a penalty of writing to the cache as well
   2. If cache is not warm, in terms on node failure or maybe taking longer to be available, the cache will return null data.

