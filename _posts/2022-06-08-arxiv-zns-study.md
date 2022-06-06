---
layout: default
title: "New arXiv study on first impressions with Zoned Namespace (ZNS) flash devices"
category: news
tags: whatsnew
permalink: /2022-june-zns-study/
---

## New arXiv study on first impressions with Zoned Namespace (ZNS) flash devices

A new technical report is available that documents our first experiences setting up and benchmarking NVMe Zoned Namespace (ZNS) flash devices. The report is available at [https://arxiv.org/abs/2206.01547](https://arxiv.org/abs/2206.01547).


**Title:** Understanding NVMe Zoned Namespace (ZNS) Flash SSD Storage Devices

**Authors:** Nick Tehrany (TU Delft) and Animesh Trivedi (VU, Amsterdam) 

**Abstract:** The standardization of NVMe Zoned Namespaces (ZNS) in the NVMe 2.0 specification presents a unique new addition to storage devices. Unlike traditional SSDs, where the flash media management idiosyncrasies are hidden behind a flash translation layer (FTL) inside the device, ZNS devices push certain operations regarding data placement and garbage collection out from the device to the host. This allows the host to achieve more optimal data placement and predictable garbage collection overheads, along with lower device write amplification. Thus, additionally increasing flash media lifetime. As a result, ZNS devices are gaining significant attention in the research community.
However, with the current software stack there are numerous ways of integrating ZNS devices into a host system. In this work, we begin to systematically analyze the integration options, report on the current software support for ZNS devices in the Linux Kernel, and provide an initial set of performance measurements. Our main findings show that larger I/O sizes are required to saturate the ZNS device bandwidth, and configuration of the I/O scheduler can provide workload dependent performance gains, requiring careful consideration of ZNS integration and configuration depending on the application workload and its access patterns. Our dataset and code are available at [https: //github.com/nicktehrany/ZNS-Study](https: //github.com/nicktehrany/ZNS-Study).



[PDF](https://arxiv.org/pdf/2206.01547.pdf) 


### Acknowledgement
This work is generously supported by Western Digital (WD) donations. Matias Bjørling and the ZNS team at Western Digital provided many helpful and explanatory comments during the course of this study. We also thank Hans Holmberg for providing comments and feedback on the report. Animesh Trivedi is supported by the NWO grant number OCENW.XS3.030, Project Zero: Imagining a Brave CPU-free World!
