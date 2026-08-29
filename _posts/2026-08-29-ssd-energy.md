---
layout: default
title: "📝 New IISWC 2026 paper energy usage of modern NVMe SSDs ⚡️"
category: news
tags: whatsnew
permalink: /2026-aug-ssd-energy/
---

## 📝 New IISWC 2026 paper on energy efficient of modern NVMe SSDs

*Ever wondered how much energy your NVMe storage workloads actually consume? ⚡️*

Our work dives into the energy efficiency of NVMe SSDs across the Linux storage stack, exploring how I/O patterns, power states, schedulers, filesystems, and applications impact energy use. We find that maximizing I/O bandwidth generally improves SSD, CPU, and server efficiency—but the best configuration depends heavily on the device and workload. We also introduce **nvme-energy-bench, an open-source framework** to help practitioners measure and optimize storage energy efficiency on their own hardware. This work is accepted to be published at the 2026 IEEE International Symposium on Workload Characterization (IISWC'26), [https://iiswc.org/iiswc2026/](https://iiswc.org/iiswc2026/). 



**Title:** Characterizing Energy Efficiency Trade-offs in the Linux Storage Stack for Flash-based NVMe SSDs


**Authors:** Joseph Kanichai∗ (VU Amsterdam), Krijn Doekemeijer∗ (VU Amsterdam), Steven van der Vlugt (ASTRON - Netherlands Institute for Radio Astronomy), Dante Niewenhuis (VU Amsterdam), Tiziano De Matteis (VU Amsterdam) , Animesh Trivedi (IBM Research, Zurich)

* Equal contributions. 

**Abstract:** Data centers (DCs) consume a large and growing share of global energy. Within DCs, storage already accounts for 5–9% of total DC energy, making storage optimization an important lever to reduce DC energy use. In this work, we focus on improving the energy efficiency of high-performance storage, where flash-based NVMe SSDs are the state-of-the-practice storage devices. To achieve this improvement, practitioners need to understand the impact of their software configurations on the efficiency of such storage. However, such understanding is limited for NVMe. Specifically, the storage stack exposes many individual knobs, while commonly conducted single source measurements further obscure which hardware component changes efficiency. In this work, we address this gap, enabling practitioners to understand how to make their storage workloads more energy efficient. First, we characterize the energy efficiency trade-offs for storage knobs across the Linux storage stack using 5 commercially available consumer and datacenter SSDs, including I/O access patterns, hardware-specific knobs such as DVFS and NVMe power states, I/O schedulers, I/O control, I/O interfaces, filesystems, and applications. We further attribute energy-efficiency changes separately to the SSD, CPU, and whole server. From this characterization, we make 7 observations for NVMe workloads. Across our 7 observations, we find that maximizing I/O bandwidth generally improves SSD, CPU, and server efficiency, while configuration efficiency remain component and device specific. Second, to enable practitioners to reproduce our characterization and extend it with additional experiments on their own hardware setup, we introduce **nvme-energy-bench, a benchmark orchestration framework**. Its design is modular, allowing practitioners to add or remove sensors as needed and to incorporate custom workloads easily. All our code is open source and available at [https://github.com/atlarge-research/nvme-energy-bench](https://github.com/atlarge-research/nvme-energy-bench).


**Paper PDF:** to come soon 
