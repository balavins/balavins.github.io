---
title: "My Essential System Tools and Papers List"
---

### Tools
I use `perf` and `vtune` pretty often for performance debug
`perf` is a lot easier and can be installed easily on all linux distros.  
 [Here](https://www.brendangregg.com/perf.html) is good list on frequently used commands.  
`valgrind` is one of my goto tool for checking memory leak 
`nmon` for disk usage for disk usage.  
[Heaptrack](https://github.com/KDE/heaptrack) can be used to find hotspots in application memory usage. Here is a cool [tutorial](https://www.youtube.com/watch?v=myDWLPBiHn0) video.  
I have wanted to play with [eBPF](https://ebpf.io) for sometime now. Plenty of cool things have been done with eBPF
[The	Next	Linux	Superpower:eBPF Primer](https://www.usenix.org/sites/default/files/conference/protected-files/srecon16europe_slides_goldshtein_linux.pdf)    
A pretty good source of eBPF has been this [website](https://www.brendangregg.com/ebpf.html) and this [video](https://www.youtube.com/watch?v=JRFNIKUROPE) by Brendan Gregg. If you haven't tried out flamegraphs from his site, would recommend you to try it. 
There is a dedicated website for eBPF that I found recently [ebpf.io](https://ebpf.io/)  

PCIe traffic measurement has always been a pain point. The best online tool I have come across has been [pcm](https://github.com/opcm/pcm). The granularity in this tool could 
also be an issue. If your application is saturating PCIe for an entire duration, the results tend to be accurate, however if it is saturating in smaller intervals, I have observed
pcm report weird results. An easier approach, if only one process is saturating the PCIe, might be to profile the amount of send and receive data in the application and measure from that.   

Depending on your need, system tools could probably be found Intel site [here](https://software.intel.com/content/www/us/en/develop/tools/catalog.html). 

[Interactive linux kernel APIs](https://makelinux.github.io/kernel/map/)


### Papers
[An analysis of performance evolution of Linux's core operations](https://dl.acm.org/doi/10.1145/3341301.3359640)
Interesting statements I found in the above paper
```
All kernel operations are slower than they were four years ago (version 4.0), except for big-write and big-munmap. The majority (75%) of the kernel operations are slower than seven years ago (version 3.0). Many of the slowdowns are substantial…
```

One more reason why offloading to accelerators could be important

```
For example, the "select"
system call is 100% slower than it was just two years ago. 
An in-depth analysis shows that over the past seven years, core
kernel subsystems have been forced to accommodate an increasing number of security enhancements and new features
```

[LegoOS: A Disseminated, Distributed OS for Hardware Resource Disaggregation](https://www.usenix.org/conference/osdi18/presentation/shan)

[DAMON: Data Access Monitor](https://sjp38.github.io/post/damon/)     
Pretty interesting tool. I would like to use this profiler and observe heatmap and wss of Apache Spark and other frameworks.


[DAMOV: A New Methodology and Benchmark Suite for Evaluating Data Movement Bottlenecks](https://arxiv.org/pdf/2105.03725.pdf)


[Accurate Throughput Prediction of Basic Blocks on Recent Intel Microarchitectures](https://arxiv.org/pdf/2107.14210.pdf)
Came to know about this paper while listening to this [podcast](https://cppcast.com/performance-tuning/)
More info could be found at [here](https://uops.info/index.html) and [here](https://github.com/andreas-abel/uiCA)

I bookmark the following sites to keep track of the best papers in this field [link](https://www.usenix.org/conferences/best-papers) [link2](https://www.sigops.org/awards/hof/)
