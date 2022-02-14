---
layout: default
title: Advanced Network Programming (ANP) course webpage
custom_title: Advanced Network Programming (ANP) course webpage
permalink: /course-anp/
---

## Advanced Network Programming Homepage (XB_0048)

In our deeply interconnected world, many details of networking may appear cryptic to its users. In Sep-Oct 2020, together with [Lin Wang](https://linwang.info/), I designed and gave a new course called [Advanced Network Programming](https://studiegids.vu.nl/en/2020-2021/courses/XB_0048) for BSc. final year students at VU Amsterdam. Advanced Network Programming (ANP) course is aimed at teaching students about the recent networking research (research-oriented teaching) in general-purpose cloud computing. At the same time with the practical work, students are trained in state-of-the-practice networking tools used in everyday Linux networking stack (tcpdump, ping, traceroute, arping, netcat). 

<p align="center">
  <img width="200" src="/images/2021-anp.png" alt="The networking stack">
  <b>Figure 1: Topics covered in ANP course</b> 
</p>

### Lecture slides 
Advanced Network Programming (ANP) ([VU catalogue](https://studiegids.vu.nl/en/2020-2021/courses/XB_0048)) is a BSc-level course. The goal of the course is to (i) make students aware of the internals of end-host and data center networking advancements; (ii) show practical tools to debug and analyze the Linux stack; (iii) teach low-level nitty and gritty details by implementing network protocols. We cover the following topics (2021, Animesh covers lecture 1-6, Lin covers lectures 7-11):

  1. **Introduction:** Evolution of socket, DMA, Interrupt storms, SGE capabilities.
  2. **Networking Concepts:** MTU, Segmentation, stateful and stateless Offloading.
  3. **Linux Internals:** NAPI, SoftIRQs, SKB, rx/tx paths, zcopy stacks.
  4. **Multicore Networking:** Interrupt balancing, multi-queue NICs, RSS, RPS, XFS, MegaPipe.
  5. **Userspace Stacks:** Packet processing, Netmap, DPDK, mTCP.
  6. **RDMA Networking:** RDMA networking, low-latency networking, history.
  7. **Network Forwarding and Routing:** Switching, STP, VLAN, IP forwarding, Router architecture.
  8. **Software Defined Networking:** SDN, OpenFlow, Network virtualization, FlowVisor.
  9. **Programmable Data Plane:** Introduction to programmable switches (PISA) and P4 language.
  10. **Cloud Networking:** Datacenter topologies, Fat tree, PortLand, Google's cloud networking.
  11. **Beyond Networking:** Video streaming internals, CBR, ABR, RTP, DASH, AWStream.
  
Editable versions of slides 1-6 are available here [https://drive.google.com/drive/folders/1bnbdM4PWpd4khDjaApou0ZYL-rOBsY4b?usp=sharing](https://drive.google.com/drive/folders/1bnbdM4PWpd4khDjaApou0ZYL-rOBsY4b?usp=sharing). Others to follow soon... 

### Practical Work 

In the course project students develop a working TCP/IP protocol in the userspace. The project consists of five key milestones:

 1. **Welcome to the machine**: setup the coding infrastructure and familarize yourself with Linux networking tools (tcpdump, ping, traceroute, arping, netcat) and RFC 793.
 2. **Is anyone out there?**: implement the ARP protocol and resolve IP addresses to mac addresses. 
 3. **Hey you**: implement socket(), connect() calls with the TCP three-way handshake
 4. **Careful With That Data, Eugene**: implment send(), recv(), and close() calls with acknowledgements, retransmission, timeouts. 
 5. **Navigating Through the Fog**: implement packet drop, retransmission, and routing using P4 and run end-to-end tests with the ANP TCP stack. 

Drop me an email if you want access to more project related resources. 

### License  
This course content are distributed under the Creative Commons Attribution 4.0 International (CC BY 4.0), [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

<!-- ### Acknowledgement
The project work is generously supported by Western Digital with their donation of ZNS devices and software support. 
-->
