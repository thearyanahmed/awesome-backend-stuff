# Distributed Systems 101

A distributed system is a collection of computers, working together. For the end-user, it behaves like a single computer is doing the work.

They all have one shared state and operate concurrently.

**Note** An important part of distributed systems is the CAP theorem. Which states that a distributed data store cannot simultaneously be consistent, available and partition tolerant.

### Decentralized != Distributed

Decentralized is essentially distributed on a technical level, but usually a decentralized system is **not owned by a single source**.

## Benefits of a distributed system

Distributed systems can be challenging to deploy and maintain, but there are many benefits to this design. Let’s go over a few of those perks.

- **Scaling:** A distributed system allows you to scale horizontally so you can account for more traffic.
- **Modular growth:** There is almost no cap on how much you can scale.
- **Fault tolerance:** Distributed systems are more fault tolerant than a single machine.
- **Cost effective:** The initial cost is higher than a traditional system, but because of their scalability, they quickly become more cost effective
- **Low latency:** Users can have a node in multiple locations, so traffic will hit the closet node
- **Efficiency:** Distributed systems break complex data into smaller pieces
- **Parallelism:** Distributed systems can be designed for parallelism, where multiple processors divide up a complex problem into pieces

## Design issues with distributed systems

- **Failure Handling:** Failure handling can be difficult with distributed systems because some components fail while others continue to function. This can often serve as an advantage to prevent large-scale failures, but it also lead to more complexity when it comes to troubleshooting and debugging.
- **Concurrency:** A common issue occurs when several clients attempt to access a shared resource simultaneously. You must ensure that all resources are safe in a concurrent environment.
- **Security issues:** Data security and sharing have increased risks in distributed computer systems. The network has to be secured, and users must be able to safely access replicated data across multiple locations.
- **Higher initial infrastructure costs:** The initial deployment cost of a distributed system can be higher than a single system. This pricing includes basic network setup issues, such as transmission, high load, and loss of information.

Resources:
- [What are distributed systems? A quick introduction](https://www.educative.io/blog/distributed-systems-considerations-tradeoffs#what)