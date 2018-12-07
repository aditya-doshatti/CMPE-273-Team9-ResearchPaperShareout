# FAWN: A Fast Array of Wimpy Nodes
### Team Members:
1. Aditya Doshatti
2. Anand Kumar
3. Devashish Nyati
4. Sai Harshith Reddy Gaddam
5. Zainab Khan

##### Summary:

The paper talks about FAWN (A Fast Array of Wimpy Nodes), which is novel cluster architecture for low-power data-intensive computing. FAWN couples low-power embedded nodes with flash storage to provide fast and energy efficient processing of random read-intensive workloads (such as key-value store application). The paper tells why FAWN should be used, design and implementation of FAWN-KV, a consistent, replicated, highly available, and high-performance key-value storage system built on a FAWN prototype, design and implementation of FAWN-DS, a log-structured key-value store, use of flash storage which supports fast random reads, efficient I/O and slow random writes and evaluation of FAWN acrchitecture.

##### Problem:

With the significant growth of large-scale data-intensive applications, such as high-performance key-value storage systems, the workloads of these applications which are mostly I/O intensive, requiring random access and the objects stored are usually small. The cluster serving the workloads requires both high performance as well as low cost (energy efficient). However, the requirement cannot be well met by conventional disk-based cluster (poor random access performance and low energy efficiency) and DRAM-based cluster (high expense and high energy cost). How to build a cost-effective and energy-efficient cluster for data-intensive workloads by a conventional architecture but still achieving satisfying capacity, high availability and low latency becomes the problem that this paper trying to solve.
 
##### Architecture:

FAWN consists of a number of slightly less-wimpy front-end nodes proxying requests from clients to a larger number of wimpy back-end nodes, which are arranged in a consistent-hashing ring with a set of virtual nodes for each physical node. A physical node stores a log-structured append-only record of key-value data items in a dedicated file for each virtual node it presents, using a modest amount of local flash storage (the poor performance of flash for small random writes being the primary motivation for the append-only format). The backend nodes employ chain replication along the hash circle, with front-ends sending puts sent to the head of the chain and gets to the tail.

##### Evaluation:

The paper evaluates a prototype of FAWN system of 21 nodes with different traditional systems. The performance-per-watt achieved by the prototype is well in excess of conventional systems (nearly 6 times). And the cost per node for FAWN is approximately 10 times less than conventional systems.

##### Flaws:

FAWN targets specifically for small-object, read-instensive, random-access workloads which do not require complex computations. FAWN is not suitable for random writes or for a cluster which envolves large number of writes. Also, memory-bound applications are also not suitable for FAWN due to garbage collection.

##### Application:

The FAWN-KV in this paper is a good sample application. If the number of erase time of flash devices is not a problem in face of large number of random write, I believe this power-efficient design will be well accepted in Industry.
