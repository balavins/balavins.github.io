---
title: "VLDB-2019 My Reading List"
---

Trying to put here some of the papers that I enjoyed in VLDB 2019    
[Choosing A Cloud DBMS: Architectures and Tradeoffs](http://www.vldb.org/pvldb/vol12/p2170-tan.pdf)  
The above paper does a good job of comparising popular OLAP databases, I wish they did Snowflake and Spark too. The morning paper did an section on this. So you can refer to that [post](https://blog.acolyer.org/2019/08/30/choosing-a-cloud-dbms/) I guess. 
[A Morsel-Driven Query Execution Engine for Heterogeneous Multi-Cores] (https://cs.brown.edu/~kayhan/papers/morsel_cp.pdf)
I like their approach of changing the query plan and scheduler for heterogenous devices so as to play to each other strengths. It is a very complex problem if you have a heterogenous cluster with FPGAs and GPUs. The data marshalling alone could be a nightmare. 
The authors seem to be getting good performance for Sparc M7 processor.       
[Rethinking Database High Availability with RDMA Networks](http://www.vldb.org/pvldb/vol12/p1637-zamanian.pdf) 
Paper from Michael Stonebraker and Tim Kraska. With evolution of RDMA networks, their `active memory` replication is trying to uproot conventional replication by proving that bottlneck in such systems is in CPU rather than in network. I believe this is valid in the context of OLTP and 100G networks RDMA networks. I do believe that OLAP faces a lot of network bottlenecks in frameworks like Apache Spark. What I believe in OLAP is that as the cluster size increses, shuffle becomes dominant and other operators in the SQL pipleine becomes less dominant.    
