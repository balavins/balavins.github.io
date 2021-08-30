---
title: "VLDB-2020 My Reading List"
---

The first paper I want to list here is the push based shuffle work from LinkedIn        
[Magnet: Push-based Shuffle Service for Large-scale Data Processing](http://www.vldb.org/pvldb/vol13/p3382-shen.pdf) 
I see a lot of activity in the Spark community too (https://issues.apache.org/jira/browse/SPARK-30602). Hope this goes in for Spark 3  


[AnalyticDB-V: A Hybrid Analytical Engine Towards Query Fusion for Structured and Unstructured Data](http://www.vldb.org/pvldb/vol13/p3152-wei.pdf)     
I have read about the [BlazeIt](https://cs.stanford.edu/~matei/papers/2019/cidr_blazeit_demo.pdf) video query engine at Stanford DAWN. I was pretty inspired by their approach. In this paper from Alibaba, they create a unified analytical engine for both Video and Structured data processing. The use case shown in the paper is quite interesting.


[Database Processing-in-Memory: An Experimental Study](http://www.vldb.org/pvldb/vol13/p334-kepe.pdf)    
There have been a growing interest to processing in-memory (PIM) in recent years. The authors propose that with PIM, data movement could be reduced between memory and caches and argue that it leads to time/energy savings. While the results are impressive (4 to 10X benefits for selection and projection operators), the problem is more challenging with memory interleaving and complex structured data-formats like parquet. For example with parquet, the page headers need to be processed in order to find out the end of current page. This is a complex operation that is difficult in PIM.    

[Pushing Data-Induced Predicates Through Joins in Big-Data Clusters](http://www.vldb.org/pvldb/vol13/p252-orr.pdf)
Won the best paper award. Predicate push-down leads to lower data being read. The predicates that reduce the data enormously are well-worth the effort in complexity of pushing them down the plan to scan operator. Bloom filters for join are common in [Presto](https://github.com/prestodb/presto/issues/2372) and [Hive](https://allbigdatathings.blogspot.com/2019/07/hive-challenges-bucketing-bloom-filters.html), but they induce scheduling overheads, because bloom filters are built during execution. This paper builds predicates during query compilation using meta-data that has been maintained. The results are pretty great
```
the median TPC-DS query finishes almost 2×
faster and uses 4× fewer total compute hours. 
Much larger speedups are seen on the tail. Total compute hours improves more than
latency ... because
some of the changes to parallel plans that result from reductions
in initial I/O add to the length of the critical path which increases
query latency while dramatically reducing total resource use; e.g.,
replacing pairjoins with broadcast joins eliminates shuffles but adds
a merge of the smaller input before broadcast
```

Haven't read this one yet. Plan to do so when I can.
[DIAMetrics: Benchmarking Query Engines at Scale](http://www.vldb.org/pvldb/vol13/p3285-gruenheid.pdf)
