---
layout: default
title: Advanced Network Programming (ANP) course webpage
custom_title: Advanced Network Programming (ANP) course webpage
permalink: /course-anp/
---

## Advanced Network Programming Homepage (XB_0048)

In our deeply interconnected world, many details of networking may appear cryptic to its users. In Sep-Oct 2020, together with [Lin Wang](https://linwang.info/), I designed and gave a new course called [Advanced Network Programming](https://studiegids.vu.nl/en/2020-2021/courses/XB_0048) for BSc. final year students at VU Amsterdam. Advanced Network Programming (ANP) course is aimed at teaching students about the recent networking research (research-oriented teaching) in general-purpose cloud computing. At the same time with the practical work, students are trained in state-of-the-practice networking tools used in everyday Linux networking stack (`tcpdump`, `ping`, `traceroute`, `arping`, `netcat`). 

In 2023 - the course was co-taught with [Balakrishnan Chandrasekaran](https://balakrishnanc.github.io/), [Matthijs Jansen](https://www.msjansen.com/), and [Jesse Donkervliet](https://jdonkervliet.com/). 

<p align="center">
  <img width="200" src="/images/2021-anp.png" alt="The networking stack">
  <b>Figure 1: Topics covered in ANP course</b> 
</p>

## Table of Contents
 * [Lecture Content](#lecture-content)
 * [Project](#practical-work)
 * [Open Source Material](#open-source-material)
 * [License](#license)

## Lecture Content 
The goal of the course is to (i) make students aware of the internals of end-host and data center networking advancements; (ii) show practical tools to debug and analyze the Linux stack; (iii) teach low-level nitty and gritty details by implementing network protocols. We cover the following topics in 2023 (Animesh covers lecture 1-6, Bala/Matthijs cover lectures 7-11):

  1. **Introduction:** Evolution of socket, DMA, Interrupt storms, SGE capabilities.
  2. **Networking Concepts:** MTU, Segmentation, stateful and stateless Offloading.
  3. **Linux Internals:** NAPI, SoftIRQs, SKB, rx/tx paths, zcopy stacks.
  4. **Multicore Networking:** Interrupt balancing, multi-queue NICs, RSS, RPS, XFS, MegaPipe.
  5. **Userspace Stacks:** Packet processing, Netmap, DPDK, mTCP.
  6. **RDMA Networking:** RDMA networking, low-latency networking, history.
  7. **WAN and BGP:** Inter-domain routing, internet architecture. 
  8. **Content Delivery Networks:** Caching, routing, replication, fault tolerance. 
  9. **Congestion Control:** Why congestion control, inter/intra data center considerations. 
  10. **Cellular Networks (5/6G):** Emerging cellular communication architectures. 
  11. **Networking for real-time online gaming:** Networking needs for online, real-time applications such as gaming. 
  
Editable versions of slides 1-6 are available here [https://drive.google.com/drive/folders/1o12Qgzj1xFBf-xIcAeALqUN1Gx8iMr29?usp=drive_link](https://drive.google.com/drive/folders/1o12Qgzj1xFBf-xIcAeALqUN1Gx8iMr29?usp=drive_link). Others to follow soon... 

## Practical Work 

In the course project students develop a working TCP/IP protocol in the userspace. The project consists of five key milestones:

 1. **Welcome to the machine**: setup the coding infrastructure and familarize yourself with Linux networking tools (`tcpdump`, `ping`, `traceroute`, `arping`, `netcat`) and RFC 793.
 2. **Is anyone out there?**: implement the ARP protocol and resolve IP addresses to mac addresses. 
 3. **Hey you**: implement socket(), connect() calls with the TCP three-way handshake
 4. **Careful With That Data, Eugene**: implement send(), recv(), and close() calls with acknowledgements, retransmission, timeouts. 
 5. **Another Graph in the Wall**: performance analysis of your TCP stack, and compare it with the Linux stack in terms of bandwidth and latencies offered. 

## Open source material

  * <a href="https://drive.google.com/drive/folders/1UFGzhx1paBgjHetPBIZL2UmL2VzDw7vt?usp=drive_link" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/gdrive.png" alt="" /></a> Home folder: [https://drive.google.com/drive/folders/1UFGzhx1paBgjHetPBIZL2UmL2VzDw7vt?usp=drive_link](https://drive.google.com/drive/folders/1UFGzhx1paBgjHetPBIZL2UmL2VzDw7vt?usp=drive_link).

  * <a href="https://drive.google.com/drive/folders/1o12Qgzj1xFBf-xIcAeALqUN1Gx8iMr29?usp=drive_link" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/gslides.png" alt="" /></a> Slides 1-6 (more to come later) [https://drive.google.com/drive/folders/1o12Qgzj1xFBf-xIcAeALqUN1Gx8iMr29?usp=drive_link](https://drive.google.com/drive/folders/1o12Qgzj1xFBf-xIcAeALqUN1Gx8iMr29?usp=drive_link).
  
  * <a href="https://drive.google.com/drive/folders/1DikFZmkc-jcW1biGPW_XtfHaY6dTsM9M?usp=drive_link" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/pdf.png" alt="" /></a> Project assignment [https://drive.google.com/drive/folders/1DikFZmkc-jcW1biGPW_XtfHaY6dTsM9M?usp=drive_link](https://drive.google.com/drive/folders/1DikFZmkc-jcW1biGPW_XtfHaY6dTsM9M?usp=drive_link). 
  
  * <a href="https://drive.google.com/file/d/1XCMRY38CSDWCNEgmkdUiEDni2AMuliYE/view?usp=drive_link" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/code.png" alt="" /></a> Project code base (zipped). [https://drive.google.com/file/d/1XCMRY38CSDWCNEgmkdUiEDni2AMuliYE/view?usp=drive_link](https://drive.google.com/file/d/1XCMRY38CSDWCNEgmkdUiEDni2AMuliYE/view?usp=drive_link)

## License  
This course content are distributed under the Creative Commons Attribution 4.0 International (CC BY 4.0), [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

<!-- ### Acknowledgement
The project work is generously supported by Western Digital with their donation of ZNS devices and software support. 
-->
