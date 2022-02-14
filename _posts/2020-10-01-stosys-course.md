---
layout: default
title: Storage Systems (StoSys) course webpage
custom_title: Storage System (StoSys) course webpage
permalink: /course-stosys/
---

## Storage Systems Homepage (XM_0092)

Storage System is a unique course due to its sole focus on NVM storage and its impact on research and education. We take inspiration from the 2018 **Data Storage Research Vision 2025** [report](https://dl.acm.org/doi/book/10.5555/3316807) which identifies (see section 6.1) 

*"Many students may only associate storage systems with hard disk drives or a specific file system, which is obviously less attractive compared to, say, self-driving cars. This situation is partly due to the fact that there is no clearly defined course on storage systems in the majority of universities."*

<p align="center">
  <img width="200" src="/images/new-storage-hierarchy.png" alt="The new storage hierarchy">
  <b>Figure 1: The new storage hierarchy</b> 
</p>

### Lecture slides 
Storage Systems ([VU catalogue](https://studiegids.vu.nl/en/2020-2021/courses/XM_0092)) is a MSc-level course that is first established and offered in [2020](/2020-stosys-slides). The course covers the rise of Non-Volatile Memory (NVM) storage technologies in commodity computing, their impact on system design (architecture, operating system), distributed systems, storage services, and application designs. We cover the following topics (2021):

  **1. Introduction:** History, NAND flash, internal organization, the new triangle of Storage Hierarchy. 

  **2. Host Interfacing and Software Implications:** NVMe, storage and block-layer optimizations. 

  **3. Flash FTL and Garbage Collection:** FTL and GC designs, concerns, and host-managed FTLs. 

  **4. Flash Filesystems:** Log-structured file systems, F2FS, DFS, and Nameless writes. 

  **5. Flash KV Stores:** B+ Trees, Hash Tables, and LSM trees on flash (LOCS, WiscKey, uTree, SILK). 

  **6. Byte-addressable Persistent Memories:** Optane, NVHeap, and Pmem/PMDK project.

  **7. Networked Flash:** Disaggregated storage, NVMoF, Disaggregated Flash, and FlashNet. 

  **8. Programmable Storage:** What is CSD, Willow, Biscuit, INSIDER.

  **9. Distributed Storage - I:** Distributed temporary data storage and formats (Crail and Albis). 

  **10. Distributed Storage - II:** Talks about Corfu and Tango distributed transaction systems. 
  
All slides are freely available at (under the CC license): [https://drive.google.com/drive/folders/1Ob994kg2UBFdrdgeEAReNILmCx7mSlxT?usp=sharing](https://drive.google.com/drive/folders/1Ob994kg2UBFdrdgeEAReNILmCx7mSlxT?usp=sharing).

Feel free to modify and use the slides in your course as you see fit. 

PS~ We are on a lookout for a cool course mascot...if you have ideas, drop me an email ☺︎

### Practical Work 

For the practical work, students develop an NVM flash translation layer (the essential part of any modern NVM storage device) and integrate a file system in RocksDB. There are five milestone in the practical work: 

  1. **A new device is in town** - setup the development environment with ZNS devices in QEMU and read the NVMe 1.4 and ZNS specifications, and test the nvme command to interact with nvme devices. 
  2. **I can’t read, is there a translator here?** - implement a host-side hybrid log-data FTL. The log segment is page-mapped, while the data-segment is zone-mapped. No GC at this stage. 
  3. **It’s 2021, we recycle** - implement a choice of garbage collection algorithm for your FTL. 
  4. **We love Rock(sDB) ‘n’ Roll!** - design and implement a file system on top of your FTL and integrate it with the RocksDB FileSystem API. 
  5. **Wake up, Neo** - the last milestone requires you to persist and restart your FTL and filesystem states and pass the RocksDB persistency tests. 

The project handbook is publicly available here [PDF](/files/2021/2021-stosys-handbook-2.0.pdf). Drop me an email if you want access to more project related resources. 

### License  
This course content are distributed under the Creative Commons Attribution 4.0 International (CC BY 4.0), [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

### Acknowledgement
The project work is generously supported by Western Digital with their donation of ZNS devices and software support. 
