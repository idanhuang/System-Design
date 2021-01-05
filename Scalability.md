## What is scalability
Scalability (可扩展性）is a property of a system to handle a growing amount of work by adding additional resources. Scaling can be done by either adding extra hardware or by upgrading the current system configuration. There are two ways of scaling: Horizonal Scaling and Vertical Scaling.


## Horizontal Scaling
Horizontal scaling means scaling the system by adding more machines to the pool of resources, and it is also called "scaling out". Horizonal scaling typically requires a load-balancer to distribute load (or request) among the servers within the cluster.

  - Pros
    - Load balancing: Distribute loads/requests to different servers within the cluster.
    - Resilient to failure: When one server goes down, others will be still avaiable to handle request
    - Scale well: Add up more servers and reduce depending on usage patterns.
    - High availability: Perfect for highly availability of Web application/Batch processing operations.
  - Cons
    - High network load: With remote produce calls, considerable amount of network load.
    - Data inconsistency: Data spread across several nodes, not consistent instantly.
    - Increased cost: Additional machines requre increased infrastruture and maintenance cost.
    - Additional license: Need to purchase additional licenses for operating system and so on.


## Vertical Scaling
Vertical scaling means scaling the system by adding more power (CPU, RAM, etc.) to of the existing  machine. Vertical scaling is also called "scaling up".
  - Pros
    - Less cost
    - Data consistency: Data is consistent and maintained within a single node
    - Less network load: Use Inter-process communication, less or almost no network overhead
  - Cons
    - Single point of failure: Server crash brings down entire system.
    - No load balancing
    - Doesn't scale well: Scaling invovles downtime and there is a limited capacity of a single machine


## References: 
1. https://www.section.io/blog/scaling-horizontally-vs-vertically/#:~:text=Horizontal%20scaling%20means%20scaling%20by,as%20%E2%80%9Cscaling%20up%E2%80%9D).
2. https://www.redswitches.com/blog/difference-between-horizontal-vertical-scaling#:~:text=Some%20of%20the%20reasons%20why,machines%20to%20the%20existing%20pool.
3. https://www.linkedin.com/pulse/scalability-horizontal-vs-vertical-scaling-scale-outin-khaja-shaik-/
