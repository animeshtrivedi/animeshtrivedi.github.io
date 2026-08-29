---
layout: default
title: "📝,📝 Two papers at IISWC 2025 on NVMe isolation and VectorDB!"
category: news
tags: whatsnew
permalink: /2025-aug-iiswc-papers/
---

## 📝,📝 Two papers accepted at IISWC 2025!

Our group at VU Amsterdam got two papers accepted at the 2025 IEEE International Symposium on Workload Characterization, [https://iiswc.org/iiswc2025/program.html](https://iiswc.org/iiswc2025/program.html). 


--- 

The first paper takes a deep dive into I/O isolation with Linux cgroups in the NVMe era, revealing where isolation works—and where it breaks down. We evaluate how different workloads, SSDs, and I/O configurations impact isolation, uncovering important gaps that can affect performance predictability in shared storage systems. 


**Title:** Does Linux Provide Performance Isolation for NVMe SSDs? Configuring cgroups for I/O Control in the NVMe Era

**Authors:** Krijn Doekemeijer, Zebin Ren, Tiziano De Matteis, Balakrishnan Chandrasekaran (Vrije Universiteit Amsterdam); Animesh Trivedi (IBM Research Europe, Zurich)


**Abstract:** Modern storage workloads commonly run in containers within data centers, such as machine learning, databases, caches, HPC, and serverless workloads. To facilitate the storage performance requirements (e.g., bandwidth, latency) of these workloads, data centers have adopted fast NVMe SSDs as a storage medium. At the same time, data centers virtualize and share these storage resources with multiple tenants to improve resource utilization and reduce costs. Such sharing leads to
an inherent trade-off between tenant performance isolation and SSD utilization. Although various research studies demonstrate how to achieve various performance isolation properties, such as fairness, there is neither a unified definition for performance isolation nor a benchmark. Furthermore, the isolation capabilities of state-of-the-practice I/O control mechanisms in the Linux kernel are not well understood. In this paper, we address these three challenges. First, we survey the definition of performance isolation and uncover four common performance isolation desiderata. Second, **we introduce isol-bench, a benchmark** for evaluating these desiderata for I/O control mechanisms. Third, we use isol-bench to evaluate I/O isolation for Linux’s state-of-the-practice I/O control mechanism, cgroups. From our evaluation, we are able to conclude that out of cgroups’s knobs io.cost achieves the most isolation desiderata, but has a latency overhead past CPU saturation. We open-source the source code
of isol-bench at [https://github.com/atlarge-research/isol-bench](https://github.com/atlarge-research/isol-bench).


  * <span><a href="https://atlarge-research.com/pdfs/2025-iiswc-cgroups.pdf"><img style="float: middle; width: 5%;" src="/images/pdf.svg" alt="" /></a></span>
  * IEEE : [https://ieeexplore.ieee.org/abstract/document/11242063/](https://ieeexplore.ieee.org/abstract/document/11242063/)

--- 

***Ever wondered if putting your RAG knowledge base on SSDs really means sacrificing performance? 🔍***


The second paper zooms in on storage-based vector databases, characterizing their performance, scalability, and I/O behavior on modern high-performance SSDs. We find that storage-based setups can outperform memory-based ones by up to 3.2×, but current vector databases often fail to fully utilize modern SSD bandwidth. We also show how search parameters can significantly impact both throughput and I/O—highlighting important opportunities for optimizing storage-based RAG systems.


**Title:** Storage-Based Approximate Nearest Neighbor Search: What are the Performance, Cost, and I/O Characteristics?

**Authors:** Zebin Ren (Vrije Universiteit Amsterdam); Krijn Doekemeijer (Vrije Universiteit Amsterdam, The Netherlands); Padma Apparao (Intel Corporation); Animesh Trivedi (IBM Research Europe, Zurich)


**Abstract:** Retrieval-augmented generation (RAG) has emerged as an effective method for enhancing large language models by integrating external knowledge sources to reduce the model size, avoid hallucinations, and provide an easier way to update the knowledge than fine-tuning. This external knowledge is commonly managed by vector databases, where the external knowledge is embedded into vectors and retrieved with vector similarity search. As the size of these external knowledge bases grows, the memory requirements for storing vectors and their associated indexes exceed the practical limits of main memory, prompting a shift toward storage-based solutions. Despite the adoption of storage-based solutions in modern vector databases, there have been limited systematic evaluations of the performance characteristics and I/O behavior of state-of-the-practice vector databases with storage-based setups. In this paper, we systematically characterize the performance, scalability, and I/O characteristics of these vector databases on modern SSDs that can deliver millions of I/O operations/s with less than 100 µs latency. We report 22 observations and 3 key findings that indicate: (i) vector databases with storage-based setups do not necessarily indicate lower performance than memorybased setups, for example, the storage-based setup DiskANN outperforms the memory-based setup, IVF, with up to 3.2× search throughput in Milvus, (ii) state-of-the-practice vector databases with storage-based setups require optimizations on I/O traffic to fully utilize the performance with flash SSDs, the maximum bandwidth achieved in our experiments is 1.7 GiB/s and can not saturate our benchmarked SSD, and (iii) the indexes’ search-time parameters affect both performance and I/O characteristics of vector databases, for example, when the parameter search_list increases from 10 to 100, the throughput of vector similarity search decreases up to 60.9% and the read bandwidth increases up to 3.3×. We open-source the scripts and traces of this work at: [https://zenodo.org/records/16916496](https://zenodo.org/records/16916496).


  * <span><a href="https://atlarge-research.com/pdfs/2025-iiswc-vectordb.pdf"><img style="float: middle; width: 5%;" src="/images/pdf.svg" alt="" /></a></span>
  * IEEE : [https://ieeexplore.ieee.org/document/11242094/](https://ieeexplore.ieee.org/document/11242094/)
