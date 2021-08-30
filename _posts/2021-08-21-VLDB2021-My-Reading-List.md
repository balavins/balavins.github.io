---
title: "VLDB-2021 My Reading List"
---

Lot of interesting papers this year   
[tf.data: A Machine Learning Data Processing Framework](http://vldb.org/pvldb/vol14/p2945-klimovic.pdf).   
This paper talks about ETL in the context of online ML pipelines. 
Some interesting statements I found in the paper
```
that 13% of jobs, out of the millions of jobs we analyzed, 
read at least 1 TB of input data.
This means that for a non-trivial fraction of training jobs, the input
data cannot fit in memory. Furthermore, over 96% of total compute
resources across jobs are spent in jobs that read over 1 TB of data.
```

Regarding overhead of using Spark Streaming to feed ML pipelines

```
While one could use a system
like Spark Streaming for online preprocessing and pass data
to the ML framework through an in-memory buffer, the additional
copies would have significant overhead due to the short step times
in ML training workloads. In the training workloads we have analyzed, step times less than 1 ms are not uncommon and most
workloads have step times less than 10ms. The extra copy overhead
would be especially significant in the common case where memory bandwidth is the bottleneck. 
```

I like their approach of establishing a DSL for efficient ML pipelines. The kind of operation fusion they discuss is pretty common in SQL and functional languages

```
As we gained experience with tf.data, we created several custom transformation that fuse commonly adjacent transformations
for performance reasons. These transformations are: map + batch
fusion, shuffle + repeat fusion, map + map fusion, map + filter
fusion, and filter + filter fusion. For example, the map + batch
fusion transforms d.map(𝑓 ).batch(𝑏) into map_and_batch(𝑓 , 𝑏),
which is functionally equivalent but the implementation of the
fused operator parallelizes and pipelines the copies of each element into the output batch with the processing of other batch
elements.
```
It looks like pretty much like the transforms that SQL optimizers like [catalyst](https://databricks.com/glossary/catalyst-optimizer) would do, but applied to machine learning pipelines. Their language has a functional programming model too !! However, `tf.data` also has an interesting auto-tune feature that is based on latency estimates which I haven't seen in SQL (Maybe I am wrong ??)

[Hyperspace: The Indexing Subsystem of Azure Synapse](http://vldb.org/pvldb/vol14/p3043-potharaju.pdf).  
Microsoft's indexing approach on Synapse. I want to do a reading list for indexing speficially. It seems that OLAP is moving more and more towards indexing.
Infact, Apache Pinot does a really good job of illustrating that with their highly configurable StarTree Index. It can be configured to the extremes taking us back to the OLAP cube times

[The End of Moore’s Law and the Rise of The Data Processor](http://vldb.org/pvldb/vol14/p2932-dayan.pdf)    
A really nice paper on Pliops' Extreme Data Processor(XDP) which is a storage engine processor ( Typically needed when there are databases that need lot of `put/dupdate` operations. Storage engines typically use LSM or log-index based architectures. Refer [here](https://vldb.org/pvldb/vol10/p1526-bocksrocker.pdf) and [here](https://lwn.net/Articles/353411/)) with ZSTD compression. I am excited about the potential of this processor. It seems to be that the complex operations involved in maintaining the index + log are offloaded to their XDP processor. From the paper, it looks like XDP works with any commercial SSD and any key value database framework, but unsure how seamless the integration is with databases.  With popularity of disaggregated storage, approaches like this become more and more necessary for database systems. Their results are quite remarkable.


[The Art of Balance: A RateupDBTM Experience of Building a CPU/GPU Hybrid Database Product](http://vldb.org/pvldb/vol14/p2999-lee.pdf).   
The authors have created a Heterogenous HTAP (or H<sup>2</sup>TAP ) with GPUs enabling OLAP operations and CPUs primarily on the OLTP side. One of the main challenges with such HTAP sytems is the data format for OLAP and OLTP. Their `AlphaStore` data store for OLAP and `DeltaStore` with MVCC for OLTP  approach is pretty interesting. I cannot imagine how complex the memory managment with GPU is. One particular paragraph made me smile
```
Pitfall (4): Advanced GPU’s VM facilities are not sufficient to
manage device memory locality. The separation between the
device memory and the host memory creates a challenge of GPU
memory management. A query engine only using GPU’s VM facilities can have uncontrolled performance degradations. RateupDB’s
solution is to manually manage device memory space for both data
locality and query performance.
```

Boy do I have experience in the above issue !!! This is a particularly painful issue for accelerators. Everybody ideally wants zero-copy transfers from accelerators to CPU but managing accelerator memory across multiple process can be very painful.

Their rule based join algorithms in GPU are notable. I am not sure how scalable such an approach is. It might work for TPC-H, but unsure for TPC-DS
The results are pretty interesting albeit single node. I am looking forward to seeing more from the team. 


Haven't read the following two papers. Will update this page when done.

[Jointly Optimizing Preprocessing and Inference for DNN-based Visual Analytics](http://vldb.org/pvldb/vol14/p87-kang.pdf)
A friend of mine referred this to me. Haven't fully read it yet.     

[Big Metadata: When Metadata is Big Data](http://vldb.org/pvldb/vol14/p3083-edara.pdf)   

List of VLDB papers from Intel folks can be found [here](https://www.intel.com/content/www/us/en/research/blogs/vldb-2021.html)
