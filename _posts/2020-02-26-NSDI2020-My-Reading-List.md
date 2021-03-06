---
title: "NSDI-2020 My Reading List"
---

Some papers that I found interesting:
[Building An Elastic Query Engine on Disaggregated Storage From SnowFlake](https://www.usenix.org/conference/nsdi20/presentation/vuppalapati)
This paper talks about the advantages and challenges of disaggregated storage at Snowflake.  Dataset for this paper: https://github.com/resource-disaggregation/snowset
```
Key findings from ∼70 million queries over a period of 14 contiguous days in February 2018 :
Customers submit a wide variety of query types; for example, read-only queries, write-only queries and read-write queries, each of which contribute to ∼28%, ∼13% and ∼59%, respectively, of all customer queries.
While the peak resource utilization can be high, the average resource utilization is usually low. We observe average CPU, Memory, Network Tx and Network Rx utilizations of ∼51%, ∼19%, ∼11%, ∼32%, respectively.
Intermediate data sizes can vary over multiple orders of magnitude across queries, with some queries exchanging hundreds of gigabytes or even terabytes of intermediate data. The amount of intermediate data generated by a query has little or no correlation with the amount of persistent data read by the query or the execution time of the query.
Even with a small amount of local storage capacity, skewed access distributions and temporal access patterns common in data warehouses enable reasonably high average cache hit rates (60-80% depending on the type of query) for persistent data accesses.
Several of our customers exploit our support for elasticity (for ∼20% of the clusters).
```
Watching the video is worth it. Plenty of interesting facts uncovevered by the team


[Themis: Fair and Efficient GPU Cluster Scheduling- Wisconsin Madison](https://www.usenix.org/conference/nsdi20/presentation/mahajan)
```
Themis, a new scheduling framework for ML training workloads. 
It's GPU allocation policy enforces that ML workloads complete in a finish-time fair manner, a new notion we introduce.
To capture placement sensitivity and ensure efficiency, 
Themis uses a two-level scheduling architecture where ML workloads bid on available resources that are offered in an auction run by a central arbiter. 
Our auction design allocates GPUs to winning bids by trading off fairness for efficiency in the short term, but ensuring finish-time fairness in the long term."

```

[Firecracker: Lightweight Virtualization for Serverless Applications -AWS](https://www.usenix.org/conference/nsdi20/presentation/agache)

[TCP ≈ RDMA: CPU-efficient Remote Storage Access with i10- Cornell](https://www.usenix.org/conference/nsdi20/presentation/hwang)

[Gandalf: An Intelligent, End-To-End Analytics Service for Safe Deployment in Large-Scale Cloud Infrastructure - Microsoft Azure](https://www.usenix.org/conference/nsdi20/presentation/li)

