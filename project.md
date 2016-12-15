---
layout: page
title: Projects
custom_title: Animesh Trivedi Projects
permalink: /projects/
order: 2
---
I am a part of High-performance IO Research Group called ZRLIO 
at the Zurich Research lab. Most of our group's work is open-sourced 
at [https://github.com/zrlio](https://github.com/zrlio).

## Crail
Crail is an open source user-level I/O architecture for the Apache data 
processing ecosystem designed from ground up for high-performance 
storage and networking hardware (40-100Gbps RDMA, flash, GPUs, etc).
It involves groud-up design and implementation of multiple components
and tools for Apache data processing ecosystem. More details can be 
found at [crail.io](http://www.crail.io).

## DaRPC 

Data center RPC or DaRPC is a Java library that provides ultra-low 
latency RPC for RDMA capable network interfaces. DaRPC is built on 
DiSNI. DaRPC source code is available 
[here](https://github.com/zrlio/darpc). 
 
## DiSNI

DiSNI is a Java library for direct storage and networking access 
from userpace. It currently provides an RDMA interface. Support for 
other userpace storage and networking interfaces, such as DPDK or 
SPDK, are in planning. DiSNI source code is available 
[here](https://github.com/zrlio/disni).

## SoftiWARP 
SoftiWARP (siw) is a software iWARP kernel driver and user library for 
Linux. It implements the iWARP protocol suite (MPA/DDP/RDMAP, 
IETF-RFC 5044/5041/5040) completely in software, without requiring 
any dedicated RDMA hardware. SoftiWARP source code is available 
[here](https://github.com/zrlio/softiwarp).
 
