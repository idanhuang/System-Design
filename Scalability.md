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
    - Increased cost: Additional machines requre increased infrastruture and maintenance cost.
    - Additonal license: Need to purchase additional licenses for operating system and so on.
    - High network load: With remote produce calls, considerable amount of network load.
    - Data inconsistency: Data spread across several nodes, not consistent instantly.


## Vertical Scaling
Vertical scaling means scaling the system by adding more power (CPU, RAM, etc.) to of the existing  machine. Vertical scaling is also called "scaling up".
  - Pros
  - Cons
















## Horizontal Scaling or Vertical Scaling?
When choosing between horizontal scaling and vertical scaling, there are various factors need to be considered:

- Performance

- Flexibility

- Regularity of upgrades

- Redudancy

- geographical distribution

- Cost




## Horizontal Scaling vs. Vertical Scaling

One fundamental differences between the two is that horizontal scaling requires breaking a sequential piece of logic into smaller pieces so that they can be executed in parallel across multiple machines. In many aspects, vertical scaling is easier because the logical doesn't need to change. We just run the same programs on higher-spec machines. However, there are many other factors should be considered when determining the appropriate scaling approach.


![scaling](https://github.com/idanhuang/Learning_Note/blob/main/img/scaling.jpg)

|               |  Horizontal Scaling           |  Vertical Scaling    |
| ------------- |:------------------------------| :--------------------|
| Database      | Each node only contains part of the data | Data resides on a single node and scaling is done through multi-core. i.e., spreading the load between the CPU and RAM resources of that machine |
| Downtime      | less or no downtime      |   Vertical scaling is limited to the capacity of one machine, scaling involves downtime |
| Concurrency | It involves distributing jobs across machines over the network. Several patterns associated with this model: Master/Worker*, Tuple Spaces, Blackboard, MapReduce.     |    Actor model: concurrent programming on multi-core machines is often performed via multi-threading and in-process message passing.|
| Message passing |In distributed computing, the lack of a shared address space makes data sharing more complex. It also makes the process of sharing, passing or updating data more costly since you have to pass copies of the data.|In a multi-threaded scenario, you can assume the existence of a shared address space, so data sharing and message passing can be done by passing a reference. |





## References: 
1. https://www.section.io/blog/scaling-horizontally-vs-vertically/#:~:text=Horizontal%20scaling%20means%20scaling%20by,as%20%E2%80%9Cscaling%20up%E2%80%9D).
2. https://www.redswitches.com/blog/difference-between-horizontal-vertical-scaling#:~:text=Some%20of%20the%20reasons%20why,machines%20to%20the%20existing%20pool.
3. https://www.linkedin.com/pulse/scalability-horizontal-vs-vertical-scaling-scale-outin-khaja-shaik-/
