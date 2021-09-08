Some posts and links that I often refer too and I find useful to dig into basics  

You can find a more thorough list of great database papers at [here](https://github.com/rxin/db-readings)

[Everything You Always Wanted to Know About Compiled and Vectorized Queries But Were Afraid to Ask](http://www.vldb.org/pvldb/vol11/p2209-kersten.pdf)
I like this paper because I used to work on this and had holes in my knowledge about code-generation and vectorization. I was familiar with the code generation that happens in Apache Spark. This link: [Apache Spark as a Compiler: Joining a Billion Rows per Second on a Laptop](https://databricks.com/blog/2016/05/23/apache-spark-as-a-compiler-joining-a-billion-rows-per-second-on-a-laptop.html) is a good source that explains basics of code generation in Spark. I want to capture the summary of the paper as it holds true for a lot of scenarios

```
 In the following, we summarize some of our main findings:
< Computation: Data-centric compiled code is better at computationally-intensive queries, as it is able to keep data in registers
and thus needs to execute fewer instructions.
> Parallel data access: Vectorized execution is slightly better in
generating parallel cache misses, and thus has some advantage
in memory-bound queries that access large hash-tables for aggregation or join.
= SIMD has lately been one of the prime mechanisms employed
by hardware architects to increase CPU performance. In theory,
vectorized query execution is in a better position to profit from
that trend. In practice, we find that the benefits are small as most
operations are dominated by memory access cost.
= Parallelization: With find that with morsel-driven parallelism
both vectorized and compilation based-engines can scale very
well on multi-core CPUs.
= Hardware platforms: We performed all experiments on Intel
Skylake, Intel Knights Landing, and AMD Ryzen. The effects
listed above occur on all of the machines and neither vectorization nor data-centric compilation dominates on any hardware
platform.
Besides OLAP performance, other factors also play an important
role. Compilation-based engines have advantages in
< OLTP as they can create fast stored procedures and
< language support as they can seamlessly integrate code written
in different languages.
Vectorized engines have advantages in terms of
> compile time as primitives are pre-compiled,
> profiling as runtime can be attributed to primitives, and
> adaptivity as execution primitives can be swapped mid-flight.
```

One issue that always annoys me with code-generation (and has been covered in multiple papers), is that it becomes impossible to profile on an operator basis as
too often, they are fused together for better performance.   


[Spark SQL: Relational Data Processing in Spark](https://dl.acm.org/doi/pdf/10.1145/2723372.2742797)  
I believe this was the first paper that introduced Spark SQL features and the `Dataframe` API. 

[The Snowflake Elastic Data Warehouse](https://dl.acm.org/doi/abs/10.1145/2882903.2903741)
The first paper introducing Snowflake features to the world. Snowflake is the Mac of cloud native computing to everyone else's linux.
One of the main architectures that work with disaggregated storage and virtual warehouses. 
```
The Virtual Warehouses layer consists of clusters of EC2
instances. Each such cluster is presented to its single user
through an abstraction called a virtual warehouse (VW).
The individual EC2 instances that make up a VW are called
worker nodes. Users never interact directly with worker
nodes. In fact, users do not know or care which or how
many worker nodes make up a VW. VWs instead come in
abstract “T-Shirt sizes” ranging from X-Small to XX-Large.
This abstraction allows us to evolve the service and pricing
independent of the underlying cloud platform.
```
I cannot imagine the complexity of their tooling platform to stitch EC2 nodes and deploy their query engine on top of it.
Their execution engine seems to have all the bells and whistles of modern columnar query engines.
The section called `LESSONS LEARNED AND OUTLOOK` is a must-read. I do not want to copy paste that entire section here


[The case for RAMClouds: scalable high-performance storage entirely in DRAM](https://web.stanford.edu/~ouster/cgi-bin/papers/ramcloud.pdf)


