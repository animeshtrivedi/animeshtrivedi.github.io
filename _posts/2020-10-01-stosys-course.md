---
layout: default
title: Storage Systems (StoSys) course webpage
custom_title: Storage System (StoSys) course webpage
permalink: /course-stosys/
---

## Storage Systems Homepage (XM_0092)

Storage System is a unique course due to its sole focus on NVM storage and its impact on research and education. We take inspiration from the 2018 **Data Storage Research Vision 2025** [report](https://dl.acm.org/doi/book/10.5555/3316807) which identifies (see section 6.1) 

*"Many students may only associate storage systems with hard disk drives or a specific file system, which is obviously less attractive compared to, say, self-driving cars. This situation is partly due to the fact that there is no clearly defined course on storage systems in the majority of universities."*

<!--
<p align="center">
  <img width="200" src="/images/new-storage-hierarchy.png" alt="The new storage hierarchy">
  <b>Figure 1: The new storage hierarchy</b> 
</p>
-->

<p align="center">
  <img width="200" src="/images/storage-evolution.png" alt="The new storage hierarchy and evolution">
  Evolution of the Storage-Memory hierarchy from (a) HDD-driven hierarchy; (b) to SSD and PMEM-based storage hierarchy; to (c) modern CXL-based Storage-Memory Continuum. See Lecture-11 for details.  
</p>

## Table of Contents
* [CCGrid 2024 Paper Material](#ccgrid-2024-paper-material)
* [Lectures](#lecture-slides)
* [Practical Assignments](#practical-work)
* [All Material (slides, assignments)](#open-source-material)
* [License](#license)
* [Acknowledgment](#acknowledgement)

## CCGrid 2024 Paper Material 
We have published our experience in setting up this course at the 24th IEEE/ACM international Symposium on Cluster, Cloud and Internet Computing (CCGrid'24). Philadelphia, May 6-9, 2024, [https://2024.ccgrid-conference.org/program/](https://2024.ccgrid-conference.org/program/). Please cite the following paper when referencing this material.

  * Animesh Trivedi, Matthijs Jansen, Krijn Doekemeijer, Sacheendra Talluri, and Nick Tehrany. **Reviving Storage Systems Education in the 21st Century - An experience report**. In the Proceedings of the 24th IEEE/ACM international Symposium on Cluster, Cloud and Internet Computing (CCGrid), Philadelphia, pages 616--625, DOI: 10.1109/CCGrid59990.2024.00074, May 6-9, 2024. [https://ieeexplore.ieee.org/document/10701387](https://ieeexplore.ieee.org/document/10701387)

  * The paper is available online at: <a href="https://atlarge-research.com/pdfs/2024-stosys-education.pdf" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/pdf.svg" alt="" /></a>

  * The conference talk is available online at: <a href="https://docs.google.com/presentation/d/1XcGmP2kTrY-OW563licFKnbG05_p-jiU8E3eGHVkFY4/edit?usp=sharing" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/gslides.png" alt="" /></a>. Many thanks to Jesse Donkervliet, who presented this work on the behalf of the authors at CCGrid 2024.

## Lecture slides 

<div style="width:60%; margin: auto;">
<p align="center">
  <img src="/images/lecture-layout.png" style="height:10%;" alt="Lectures layout (L1-L11) in Storage Systems course.">
  Lectures layout (L1-L11) in Storage Systems course.  
</p>
</div>

Storage Systems is a MSc-level course that was first established and offered in [2020](/2020-stosys-slides). The course covers the rise of Non-Volatile Memory (NVM) storage technologies in commodity computing, their impact on system design (architecture, operating system), distributed systems, storage services, and application designs. We cover the following topics in the last edition of the course in 2023:

  **1. Introduction:** We introduce the historical context, HDDs, NAND/NOR/XOR flash cells and chips, media-level differences between SSDs and HDDs, SSD packaging (dies, blocks, pages, internal organization), operations (I/O, GC, and erase), and performance and endurance properties. We highlight that the storage design guidelines and tradeoffs have changed with SSDs and the new triangle of Storage Hierarchy. 

  **2. Host Interfacing and Software Implications:** We discuss how 2-3 orders-of-magnitude performance improvements of SSDs with high parallelism necessitated the development of a new host controller (NVM Express, NVMe) and the re-design of the Linux block layer (multi-queue block layer design, polling driven architecture). 

  **3. Flash FTL and Garbage Collection:** We introduce the concept of the FTL and its responsibilities for active flash chips management (built on L-1), designs in the garbage collection (GC) algorithms. We then discuss why the host software (file systems, data stores) need to be aware of the FTL design, GC operations, and trade-offs captured as the SSD Unwritten Contracts. We then look at SSD-managed, and host-managed FTL designs. A host-managed FTL design is used for their practical assignment. 

  **4. Flash Filesystems:** We discuss how SSD internal properties and FTL designs (Lectures 2 and 3) prefer sequential writes, which can be generated by log-structured file systems (LFS). We analyze LFS designs, GC, their optimizations for flash SSDs (F2FS, SFS file systems), and novel FS designs with software-defined flash such as Direct File System (DFS) and Nameless Writes. 

  **5. Flash KV Stores:** We introduce important lookup data structures (B+ tree, hash table, LSM tree) and how unique properties of flash storage (asymmetrical read/write, and high parallelism) require these structures to consider their application-level read/write amplifications and space requirements (the RUM Conjecture). We cover research projects such as LOCS, WiscKey, uTree, SILK. 

  **6. Byte-addressable Persistent Memories:** We discuss performance characterization of Intel Optane persistent memory, its impact on building novel abstractions like persistent data structures (NVHeap, PMDK) and even novel OS designs (Twizzler), thus blurring the difference between a file and memory.

  **7. Networked Flash:** We draw an analogy with Lectures-1 and 2 and establish that fast storage requires fast networks and co-designed network-storage protocols such as NVMe-over-Fabrics (NVMoF). We discuss the concept of storage/flash disaggregation and various block-level, file system-level, and application-level (RDMA) access to remote storage (FlashNet). 

  **8. Programmable Storage:** We introduce the problem of the data movement wall and the opportunity with SSDs that have an active programmable element, the FTL. Hence, a user can run its data processing program close to storage, inside an SSD with the FTL, thus enabling Computational or Programmable storage. We discuss its origins (Active Stroage, Intelligent Disks), modern interpretations (Willow, Biscuit, INSIDER), various hardware/software design options that offer performance and efficiency via specialization, and the recent efforts to standardize it.

  **9. Distributed Storage - I:** We identify the opportunity with fast storage and networks (L-7) that help distributed data processing frameworks to efficiently manage their runtime state and data exchange operations (NodeKernel and Crail). We then discuss how data storage formats become a bottleneck due to their HDD-era design assumptions, such as *“the CPU is fast and I/O is slow”* (Albis). 

  **10. Distributed Storage - II:** We link the write-once property of flash chips with the design of a transaction system and discuss networked flash-based (L-7) Corfu and Tango transaction systems. We discuss the historical context in which such systems were built, and what unique properties flash storage offers to realize these systems now (but not before). 

  **11. Emerging Topics:** we consider how NVM storage connects to wider hardware trends (CXL) and necessitates development of a new software I/O API (io_uring). CXL connects all storage and memory elements in a byte-addressable, coherent manner, thus giving rise to a new “Storage-Memory Continuum” with a highly granular performance spectrum instead of the classical triangle of cache-memory-storage hierarchy. Later, we discuss the emergence of io_uring, a new asynchronous high-performance I/O API in Linux and its design [69], [70]. These developments led to a re-division of labor among hardware-software-OS in a storage system. 


All slides are freely available at (under the CC license): [https://drive.google.com/drive/folders/1Ob994kg2UBFdrdgeEAReNILmCx7mSlxT?usp=drive_link](https://drive.google.com/drive/folders/1Ob994kg2UBFdrdgeEAReNILmCx7mSlxT?usp=drive_link).

Feel free to modify and use the slides in your course as you see fit. 


## Practical Work 

For the practical work, students develop an NVM flash translation layer (the essential part of any modern NVM storage device) and integrate a file system in RocksDB. There are five milestone in the practical work: 

  1. **A new device is in town** - setup the development environment with ZNS devices in QEMU and read the NVMe 1.4 and ZNS specifications, and test the nvme command to interact with nvme devices. 
  2. **I can’t read, is there a translator here?** - implement a host-side hybrid log-data FTL. The log segment is page-mapped, while the data-segment is zone-mapped. No GC at this stage. 
  3. **It’s 2021, we recycle** - implement a choice of garbage collection algorithm for your FTL. 
  4. **We love Rock(sDB) ‘n’ Roll!** - design and implement a file system on top of your FTL and integrate it with the RocksDB FileSystem API. 
  5. **Wake up, Neo** - the last milestone requires you to persist and restart your FTL and filesystem states and pass the RocksDB persistency tests. 

The project handbook is publicly available here [PDF](https://drive.google.com/file/d/10iRYCHMoJaUbCEK8yVUB5Hz8FBtpHh-S/view?usp=drive_link). See below for the editable version. 

## Open-source material 

  * <a href="https://drive.google.com/drive/folders/1K165plw4xDHZFZHeuhMvpqgEP8MaRBlT?usp=drive_link" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/gdrive.png" alt="" /></a> Home folder: [https://drive.google.com/drive/folders/1K165plw4xDHZFZHeuhMvpqgEP8MaRBlT?usp=drive_link](https://drive.google.com/drive/folders/1K165plw4xDHZFZHeuhMvpqgEP8MaRBlT?usp=drive_link).

  * <a href="https://drive.google.com/drive/folders/1K165plw4xDHZFZHeuhMvpqgEP8MaRBlT?usp=drive_link" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/gslides.png" alt="" /></a> All slides 2023 edition [https://drive.google.com/drive/folders/1K165plw4xDHZFZHeuhMvpqgEP8MaRBlT?usp=drive_link](https://drive.google.com/drive/folders/1K165plw4xDHZFZHeuhMvpqgEP8MaRBlT?usp=drive_link).
  
  * <a href="https://docs.google.com/document/d/19oW0B38IMWXao2LHkuiSicIoLHS9ctyw_9LdDHiwjE0/edit?usp=drive_link" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/pdf.png" alt="" /></a> Project assignment [https://docs.google.com/document/d/19oW0B38IMWXao2LHkuiSicIoLHS9ctyw_9LdDHiwjE0/edit?usp=drive_link](https://docs.google.com/document/d/19oW0B38IMWXao2LHkuiSicIoLHS9ctyw_9LdDHiwjE0/edit?usp=drive_link). 
  
  * <a href="https://drive.google.com/drive/folders/1HFMHR_UiPwXFUlpvvWr28WWSem-gdMmG?usp=drive_link" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/code.png" alt="" /></a> Project code base (zipped). [https://drive.google.com/drive/folders/1HFMHR_UiPwXFUlpvvWr28WWSem-gdMmG?usp=drive_link](https://drive.google.com/drive/folders/1HFMHR_UiPwXFUlpvvWr28WWSem-gdMmG?usp=drive_link)

## License  
This course content are distributed under the Creative Commons Attribution 4.0 International (CC BY 4.0), [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

## Acknowledgement
The project work is generously supported by Western Digital with their donation of ZNS devices and software support. 
