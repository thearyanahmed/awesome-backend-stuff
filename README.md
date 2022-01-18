# Backend Interview Preparation

   Index

   + Backend API best practices
   + Agile
   + AWS
      + Application deployment
         + Beanstalk
         + EKS
         + VPC & Networking
            + Route53
         + SQS
         + SNS
         + EC2 fleet
         + High availability & scalability
         + Beanstalk
         + S3
         + CloudFront
         + Elastic Load Balancer
   + Database
      + Common topics / problems
         + ACID
         + Lazy loading
         + N + 1 problem
         + Normalisation
      + Relational
         + MySQL
      + Non-Relational
         + Common topics
            + CAP theorem
            + NoSQL & Scalability
         + MongoDB
         + Redis
   + Frameworks
      + Laravel*
      + Symfony
      + Falcon
   + Caching
      + Caching strategies
         + Lazy Loading

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
         + Write through

            Write through is a strategy is when data is written to database, it is also written to the cache.

            *Pros*

            1. Data is never stale.

            *Cons*

            1. Every write request has a penalty of writing to the cache as well
            2. If cache is not warm, in terms on node failure or maybe taking longer to be available, the cache will return null data.
      + Caching with varnish
   + Server
      + Deployment
      + Linux basic usage
   + System Design
      + Latency & Throughput
      + Client Server Model
      + Hashing
      + Network protocols
      + Proxies
      + Load Balancers
      + Replication & Sharding
      + Logging & Monitoring
      + MapReduce
      + Pub/Sub
   + Code design
      + TDD
      + Coupling
      + Early testing
      + OOP
   + [SOLID](solid.md)
   + Design patterns
      + Inheritance vs composition
      + Singleton
   + Language
      + PHP
      + Go
         + Buffered channels vs Unbuffered channels
   + Git
      + Difference between fetch & pull
      + What is git rebase
      + What is upstream
   + SQL
   + Kafka
   + Prometheus
   + Grafana
   + Concurrency
      + Race conditions
      + Deadlocks
      + Process starvation
   + Distributed systems
      + What are distributed systems?
      + Testing distributed systems.
      + Async communication
      + Pitfalls of RPC
      + The design
      + Fault tolerance
      + Failures
      + Network partitions
      + Request / Reply vs Pub / Sub
      + Transactions
      + mapReduce
   + Docker
   + Kubernetes
      + K8s
         + SSL on k8s
         + Node
         + ConfigMap
         + Cluster
         + Pod
         + Master
         + MultipleMaster
      + Helm
   + Lifecycle
      + Agile
   + Data structures & algorithms
      + FIFO n LIFO
      + Stackoverflow
      + Tail recursive n!
      + REPL (?)
      + Memory leaks
      + PRNG
      + Garbage collection
      + Sorting huge files
      + Simple web server
      + Graph
         + Tree
         + BFS
         + DFS
         + Dijkstra’s
   + Software Architecture
      + No cache
      + Event driven
      + Failures user sessions
      + CQRS
      + Emergent and Evolutionary
      + Scale-out, Scale-up
      + CPUs
      + Pub/Sub
      + Vendor lock-in
   + Service oriented architecture
      + Long lived transactions
      + SOA and Microservices
      + Too micro
      + Microservice architecture
   + Security
      + Don’t invent Cryptography
      + 2-FA
      + SQLi
      + Detect SQLi
      + XSS
      + CSRF
      + HTTPs
      + MITM
      + Stealing sessions
   + General
      + TCP sockets
      + Real time communication


