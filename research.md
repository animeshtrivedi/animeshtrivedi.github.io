---
layout: default
title: Research of Animesh Trivedi
custom_title: Research of Animesh Trivedi
permalink: /research/
---

<!-- 
I am a part of High-performance IO Research Group called ZRLIO at the Zurich Research lab. Most of our group’s work is open-sourced at [https://github.com/zrlio](https://github.com/zrlio). -->

I have the following active research projects:

### Efficient Machine Learning from Modern Storage Devices
In machine learning, large models are associated with more accuracy and intelligence. Building and training of large models processes large amounts of data in CPU-attached and accelerator on-board DRAM memories, which are not scalable, energy-inefficient, and extremely expensive, thus putting large model training out of reach for many users. How can we leverage Non-Volatile Memory (NVM) storage technology to design a Machine-learning-from-Storage model training paradigm, where data is dynamically moved between NVM storage and DRAM memories on-demand, thus building a new class of cost- and energy-efficient system?


This is a [NWO funded project](https://www.nwo.nl/en/news/sixteen-innovative-research-projects-launched-through-domain-science-klein-0) for €350,000. 

### Stratus : Clouds with Microarchitectural Resource Management
The emerging next generation of cloud services like Granular and Serverless computing are pushing the boundaries of the current cloud infrastructure. In order to meet the performance objectives, researchers are now leveraging low-level hardware microarchitectural resources in clouds. At the same time these resources are also a major source of security problems that can compromise the confidentiality and integrity of sensitive data in multi-tenant shared cloud infrastructures. The core of the problem is the lack of isolation due to the unsupervised sharing of microarchitectural resources across different performance and security boundaries. In this work, we propose to build Stratus clouds that treat the isolation on microarchitectural elements as the key design principle when allocating cloud resources. This isolation improves both performance and security, but at the cost of reducing resource utilization. Stratus captures this trade-off using a novel abstraction that we call isolation credit, and shows how it can help both providers and tenants when allocating microarchitectural resources using Stratus’s declarative interface. There are multiple implementation, mechanisms, policies challenges associated with building Stratus that we explore in this work. 

  * [HotCloud 2020 paper](https://www.usenix.org/conference/hotcloud20/presentation/razavi)

### Zero-CPU or CPU-free Computing 
Since the beginning of computing, we have relied on the CPU for data processing. As the CPU performance improved over the decades, so did our data processing capabilities. However, we are hitting a plateau where not only the performance gains are stalling, but the CPU is now considered a major source of inefficiencies and security vulnerabilities. In this project, we are envisioning a world without CPUs. A CPU-free computing architecture can completely eliminate the CPU (0% usage) and associated inefficiencies from computing. The project will revolutionize the way computation is done by building a first-of-its-kind CPU-free data-processing application that leverages modern domain-specific, programmable non-CPU devices and accelerators available today. 

This is a [NWO funded project](https://www.nwo.nl/en/news/sixteen-groundbreaking-research-projects-launched-through-third-round-nwo-open-competition-xs) for €50,000. 

I am working in collaboration with [Marco Spaziani Brunella](https://marcospazianibrunella.github.io/) (University of Rome Tor Vergata) to design and build the first prototype of a distributed application. 

  * Hyperion vision document [write up](/2022-may-hyperion-vision/)
  * Systems for Post-Moore Architectures (SPMA'22) [write up](/2022-march-spma22/) 

### Griffin : A Data Sharing Service at the Edge 
Edge computing is an emerging computing paradigm where data is generated and processed in the field using distributed computing devices. Many applications such as real-time video processing, augmented/virtual reality gaming, environment sensing, benefit from such decentralized, close-to-user deployments where low-latency, real-time results are expected. As with any distributed application, one of the key challenges in the development of collaborative applications is how to efficiently share data and state among multiple edge clients. The dynamic and heterogeneous environment together with diverse application’s requirements make data sharing at the edge a challenging problem. In comparison to the cloud, where there are more than half of dozen services available for data sharing, how does such a service should look like at the edge? 

[HotEdge 2020 paper](https://www.usenix.org/conference/hotedge20/presentation/trivedi)


## Past projects

### High-Performance Relational Data Processing
Currently, I am investigating what would it take to process relational SQL data at the rate of 100 Gbps - the rate at which modern networking and storage devices can serve data today. As a first step, I have investigated the reading performance of file formats (JSON, Avro, Parquet, ORC, and Arrow). The finding are summarized in my [blog post](https://crail.incubator.apache.org/blog/2018/08/sql-p1.html) and our USENIX ATC 2018 [paper](https://www.usenix.org/system/files/conference/atc18/atc18-trivedi.pdf).

### Apache Crail (Incubating)
Crail is an open source user-level I/O architecture for the Apache data processing ecosystem designed from the ground up for high-performance storage and networking hardware (40-100Gbps RDMA, flash, GPUs, etc). It involves design and implementation of multiple components and tools for the Apache data processing ecosystem. More details can be found at [https://crail.incubator.apache.org/](https://crail.incubator.apache.org/).

### DaRPC
Data center RPC or DaRPC is a Java library that provides ultra-low latency RPC for RDMA capable network interfaces. DaRPC is built on DiSNI. DaRPC source code is available [https://github.com/zrlio/darpc](https://github.com/zrlio/darpc).

### DiSNI
DiSNI is a Java library for direct storage and networking access from userspace. It currently provides an RDMA interface. Support for other userspace storage and networking interfaces, such as DPDK or SPDK, are in planning. DiSNI source code is available at [https://github.com/zrlio/disni](https://github.com/zrlio/disni).

### SoftiWARP
SoftiWARP (siw) is a software iWARP kernel driver and user library for Linux. It implements the iWARP protocol suite (MPA/DDP/RDMAP, IETF-RFC 5044/5041/5040) completely in software, without requiring any dedicated RDMA hardware. SoftiWARP source code is available at [https://github.com/zrlio/softiwarp](https://github.com/zrlio/softiwarp).

### RStore 
Distributed DRAM stores have become an attractive option for providing fast data access to analytics applications. To accelerate the performance of these stores, researchers have proposed using RDMA technology. RDMA offers high bandwidth and low latency data access by carefully separating resource setup from IO operations, and making IO operations fast by using rich network semantics and offloading. Despite recent interest, leveraging the full potential of RDMA in a distributed environment remains a challenging task. 

RStore is a DRAM-based data store that delivers high performance by extending RDMA's separation philosophy to a distributed setting. RStore achieves high aggregate bandwidth (705 Gb/s) and close-to-hardware latency on our 12-machine testbed. We developed a distributed graph processing framework and a Key-Value sorter using RStore's unique memory-like API. The graph processing framework, which relies on RStore for low-latency graph access, outperforms state-of-the-art systems by margins of 2.6-4.2x when calculating Page Rank. The Key-Value sorter can sort 256 GB of data in 31.7 sec, which is 8x better than Hadoop TeraSort in a similar setting.

### FlashNet 
During the past decade, network and storage devices have undergone rapid performance improvements, delivering ultra-low latency and several Gbps of bandwidth. Nevertheless, current network and storage stacks fail to deliver this hardware performance to the applications, often due to the loss of IO efficiency from stalled CPU performance. While many efforts attempt to address this issue solely on either the network or the storage stack, achieving high-performance for networked-storage applications requires a holistic approach that considers both.

FlashNet is a software I/O stack that unifies high-performance network properties with flash storage access and management. FlashNet builds on RDMA principles and abstractions to provide a direct, asynchronous, end-to-end data path between a client and remote flash storage. The key insight behind FlashNet is to co-design the stack's components (an RDMA controller, a flash controller, and a file system) to enable cross-stack optimizations and maximize IO efficiency. In micro-benchmarks, FlashNet improves 4kB network IOPS by 38.6% to 1.22M, decreases access latency by 43.5% to 50.4 µsecs, and prolongs the flash lifetime by 1.6-5.9x for writes. We illustrate the capabilities of FlashNet by building a Key-Value store, and porting a distributed data store that uses RDMA on it. The use of FlashNet's RDMA API improves the performance of a KV store by 2x, and requires minimum changes for the ported data store to access remote flash devices.


