---
layout: default
title: Research of Animesh Trivedi
custom_title: Research of Animesh Trivedi
permalink: /research/
---

I am a part of High-performance IO Research Group called ZRLIO at the Zurich Research lab. Most of our group’s work is open-sourced at [https://github.com/zrlio](https://github.com/zrlio).

### High-Peroformance Relational Data Processing
Currently, I am investigating what would it take to process relational SQL data at the rate of 100 Gbps - the rate at which modern networking and storage devices can serve data today. As a first step, I have investgiated the reading performance of file formats (JSON, Avro, Parquet, ORC, and Arrow). The finding are summaried in my [blog post](https://crail.incubator.apache.org/blog/2018/08/sql-p1.html) and our USENIX ATC 2018 [paper](https://www.usenix.org/system/files/conference/atc18/atc18-trivedi.pdf).

### Apache Crail (Incubating)
Crail is an open source user-level I/O architecture for the Apache data processing ecosystem designed from ground up for high-performance storage and networking hardware (40-100Gbps RDMA, flash, GPUs, etc). It involves groud-up design and implementation of multiple components and tools for Apache data processing ecosystem. More details can be found at [https://crail.incubator.apache.org/](https://crail.incubator.apache.org/).

### DaRPC
Data center RPC or DaRPC is a Java library that provides ultra-low latency RPC for RDMA capable network interfaces. DaRPC is built on DiSNI. DaRPC source code is available [https://github.com/zrlio/darpc](https://github.com/zrlio/darpc).

### DiSNI
DiSNI is a Java library for direct storage and networking access from userpace. It currently provides an RDMA interface. Support for other userpace storage and networking interfaces, such as DPDK or SPDK, are in planning. DiSNI source code is available at [https://github.com/zrlio/disni](https://github.com/zrlio/disni).

### SoftiWARP
SoftiWARP (siw) is a software iWARP kernel driver and user library for Linux. It implements the iWARP protocol suite (MPA/DDP/RDMAP, IETF-RFC 5044/5041/5040) completely in software, without requiring any dedicated RDMA hardware. SoftiWARP source code is available at [https://github.com/zrlio/softiwarp](https://github.com/zrlio/softiwarp).
