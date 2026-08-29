---
layout: default
title: "📝 New EuroMLSys 2026 paper on simulating GenAI platforms"
category: news
tags: whatsnew
permalink: /2026-april-opal/
---

## 📝 New EuroMLSys 2026 paper on simulating distributed GenAI platforms 

*What if we could explore the rapidly evolving world of distributed GenAI systems without constantly needing expensive hardware?*

Our new paper, **“A Case for a Simulation-Driven Exploration of Distributed GenAI Platforms,”** presents Opal, a pure python-based simulator for exploring LLM inference platforms, policies, configurations, and what-if scenarios at scale. Opal enables researchers to study complex trade-offs across compute, KV-cache management, storage, networking, performance, cost, and energy—before deploying on real infrastructure.


**Title:** A Case for a Simulation-Driven Exploration of Distributed GenAI Platforms


**Authors:** Animesh Trivedi, Radu Stoica, Jeremy Cohn, Danny Harnik, Yue Zhu, Jonathan Terner (IBM Research); Guy Margalit (IBM Storage); Frank Schmuck, Vasily Tarasov, Swaminathan Sundararaman (IBM Research)


**Abstract:** The rapid adoption of Generative AI (GenAI) workloads has driven the emergence of inference serving platforms like llm-d and Nvidia Dynamo. However, exploring the design space for these platforms, especially for large-scale, multi-layer optimizations, remains prohibitively expensive and slow due to limited hardware access and high engineering overheads. Current evaluation methods often focus on isolated components, failing to capture the complex interplay between hardware components, scheduling policies, and dynamic GenAI workloads.
We argue that the design space exploration of GenAI platforms can be accelerated by leveraging a simulation-based approach that offers a fast, cheap, and scalable methodology to rapidly prototype and validate new ideas. To this end, we present Opal, an open-source, discrete-event simulation framework. Unlike prior simulators, Opal models interactions across multiple layers of the inference stack from hardware to workloads, enabling a holistic analysis of system-level behaviors and trade-offs. Opal is designed to be simple, extensible, reproducible, and fast, allowing researchers to rapidly explore a wide range of deployment scenarios and optimization strategies. In this paper, we present our motivation and Opal's design, and seek feedback from the community on open challenges. 


Opal is freely available (Apache 2.0) at [https://github.com/IBM/opal-sim](https://github.com/IBM/opal-sim)


<span><a href="https://dl.acm.org/doi/epdf/10.1145/3805621.3807623"><img style="float: middle; width: 5%;" src="/images/pdf.svg" alt="" /></a></span>


ACM: [https://doi.org/10.1145/3805621.3807623](https://doi.org/10.1145/3805621.3807623)
