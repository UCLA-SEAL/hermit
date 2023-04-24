# Hermit
Hermit: Low-Latency, High-Throughput, and Transparent Remote Memory via Feedback-Directed Asynchrony ([NSDI 2023](https://www.usenix.org/conference/nsdi23/presentation/qiao))

## Summary
Remote memory techniques are gaining traction in datacenters because they can significantly improve memory utilization. A popular approach is to use kernel-level, page-based memory swapping to deliver remote memory as it is transparent, enabling existing applications to benefit without modifications. Unfortunately, current implementations suffer from high software overheads, resulting in significantly worse tail latency and throughput relative to local memory.

Hermit is a redesigned swap system that overcomes this limitation through a novel technique called adaptive, feedback-directed asynchrony. It takes non-urgent but time-consuming operations (e.g., swap-out, cgroup charge, I/O deduplication, etc.) off the fault-handling path and executes them asynchronously. Different from prior work such as Fastswap, Hermit collects runtime feedback and uses it to direct how asynchrony should be performed—i.e., whether asynchronous operations should be enabled, the level of asynchrony, and how asynchronous operations should be scheduled. We implemented Hermit in Linux 5.14. An evaluation with a set of latency-critical applications shows that Hermit delivers low-latency remote memory. For example, it reduces the 99th percentile latency of Memcached by 99.7% from 36 ms to 91 µs. Running Hermit over batch applications improves their overall throughput by 1.24× on average. These results are achieved without changing a single line of user code.

## Team
This project is done in collaboration with Professor [Harry Xu](http://web.cs.ucla.edu/~harryxu/)'s group at UCLA. Please visit [Hermit project at UCLA Systems](https://github.com/uclasystem/hermit). If you encounter any problems, please open an issue or feel free to contact us:

[Yifan Qiao](https://web.cs.ucla.edu/~yifan/): PhD student, [yifanqiao@ucla.edu](mailto:yifanqiao@ucla.edu).

## How to cite 
Please refer to our NSDI'23 paper, **[Hermit: Low-Latency, High-Throughput, and Transparent Remote Memory via Feedback-Directed Asynchrony](https://www.usenix.org/system/files/nsdi23-qiao.pdf)** for more details. 

### Bibtex  
```txt
@inproceedings {qiao2023hermit,
author = {Yifan Qiao and Chenxi Wang and Zhenyuan Ruan and Adam Belay and Qingda Lu and Yiying Zhang and Miryung Kim and Guoqing Harry Xu},
title = {Hermit: {Low-Latency}, {High-Throughput}, and Transparent Remote Memory via {Feedback-Directed} Asynchrony},
booktitle = {20th USENIX Symposium on Networked Systems Design and Implementation (NSDI 23)},
year = {2023},
isbn = {978-1-939133-33-5},
address = {Boston, MA},
pages = {181--198},
url = {https://www.usenix.org/conference/nsdi23/presentation/qiao},
publisher = {USENIX Association},
month = apr,
}
```
