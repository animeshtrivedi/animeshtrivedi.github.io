---
layout: default
---
{% raw %}
<a href="/images/2020-atr-image.png" title="View larger picture"><img src="/images/2020-atr-image.png" alt="Photo of Animesh Trivedi"
style="float:right;width:25%;max-width:150px;margin-left:15px;"/></a>
{% endraw %}

<!-- <mark><b>Update:</b></mark> Starting from 2019, I will be joining the Department of Computer Science, VU, Amsterdam as (tenure-track) Assistant Professor. -->

I am an Assistant Professor (tenured) at the [CompSys Section](https://www.vucompsys.net/) in the [Department of Computer Science, VU, Amsterdam](https://www.cs.vu.nl/en/index.aspx). 

My main research areas are in storage, networking, operating systems, and distributed systems. Broadly speaking, I am interested in the performance aspect of systems, spanning from multi-core CPUs to distributed systems. Currently, I have following active interests 
  * how to leverage fast and cheap NVM storage (flash, optane) in data-heavy ML workloads
  * how design and build foundational software services for Edge computing
  * how to design next-generation of systems software for modern, programmable devices

I am a member of the [IPN EDI (equity, diversity, inclusion) working group](https://ict-research.nl/edi-working-group/).

<!--am investigating how modern, programmable, high-performance devices (100+ Gbps network, NVMe/Flash/Optane storage, etc.) can be leveraged in large-scale data-processing and machine learning systems such as Spark, Tensorflow, serverless workloads. 

I am one of the founding contributors of the [Apache Crail (Incubating)](https://crail.incubator.apache.org/) project. Prior to joining VU, I was a Researcher at the IBM Research Lab, Zurich. I obtained my PhD and MSc in Computer Science at ETH Zurich.
Prior to joining VU, I was a Researcher at the IBM Research Lab, Zurich. I obtained my PhD and MSc in Computer Science at ETH Zurich.
finished my PhD in Computer Science at ETH Zurich under the supervision of Prof. Thomas Gross.-->

<img style="float: middle; width: 8%;" src="/images/vu.png" alt="" /> <b>students:</b> If you would like to work on storage systems (NVMe, ZNS, flash, optane, SSDs, file systems, key-value stores), distributed systems (high performance storage, networking) and data-processing frameworks as (a) thesis work ([XM_0011](https://studiegids.vu.nl/en/Master/2021-2022/computer-science-joint-degree/XM_0011#/)); (b) individual research course ([XM_405088](https://studiegids.vu.nl/en/Master/2021-2022/computer-science-joint-degree/XM_405088#/)) work; or (c) literature survey work at VU ([X_405111](https://studiegids.vu.nl/en/Master/2021-2022/computer-science-joint-degree/X_405111#/)) - drop me an email. Also [my advice](/advice/) for working with me, and other [useful resources for students](/teaching).


<img style="float: middle; width: 4%;" src="/images/slack.svg" alt="" /> **CompSysNL Slack:** If you are a computer systems researcher in the Netherlands, please consider joining the CompSys NL slack [https://compsys-nl.slack.com/](https://compsys-nl.slack.com/), [[joining link](https://join.slack.com/t/compsys-nl/shared_invite/zt-fx78q58g-Veea9LReM5zA1QqRPQ6peA)].

**Research Funding:** My research is generously funded by the Dutch Research Council (NWO), SURF, Western Digital, Xilinx, Amazon, and Mellanox - thank you all! 

<!-- 
### Sticky  
  * [<mark>PhD Opening</mark> in the area of NVM storage support for ML](https://workingat.vu.nl/ad/phd-position-in-storage-support-for-machine-learning/w3s7ih), (**deadline: June 15th, 2021**).
  * <mark>CompSys'21 is happening</mark> (June 28th/29th 2021), see [the announcement](/compsys2021-announcement/).
-->

### <img style="float: middle; width: 5%;" src="/images/sticky.png" alt="" /> Sticky    
  * **CPU-free Computing**: *Hyperion: A Case for Unified, Self-Hosting, Zero-CPU Data-Processing Units (DPUs)*, [https://arxiv.org/abs/2205.08882](https://arxiv.org/abs/2205.08882), 2022, <a href="https://arxiv.org/pdf/2205.08882.pdf" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/pdf.svg" alt="" /></a>.

  * **Dutch CompSys Research Manifesto**, *Future Computer Systems and Networking Research in the Netherlands: A Manifesto*, [https://arxiv.org/abs/2206.03259](https://arxiv.org/abs/2206.03259), 2022, <a href="https://arxiv.org/pdf/2206.03259" target="_blank" rel="noopener noreferrer" style="background-color:white; color:white;font-weight:bold"><img style="float: middle; width: 3%;" src="/images/pdf.svg" alt="" /></a>.
    * 2-page executive summary ([PDF](https://bit.ly/ManifestoCompSysNLSummary)), Flyer ([PDF](https://bit.ly/CompSysNLFlyerA4))

  * **Modern Storage System (StoSys)** course lectures are publically available on my [teaching page](/course-stosys). If you are interested in setting up such a course, drop me an email to share project material. 
  
### What is new
<ul class="news list-unstyled">
{% for post in site.tags.whatsnew limit: site.front_page_news %}
    {% if post.shortnews %}
        <li class="shortnews">
            <span class="date">{{ post.date | date: "%B %-d, %Y" }}</span>
            {{ post.content }}
        </li>
    {% else %}
        <li class="bloglink">
            <span class="date">{{ post.date | date: "%B %-d, %Y" }}</span>
            <a href="{{ post.url }}">&raquo; {{ post.title }}</a>
        </li>
    {% endif %}
{% endfor %}
</ul>
{% assign numposts = site.categories.news | size %}
{% if numposts >= site.front_page_news %}
<p><a href="{{ site.base }}/news/">more posts&hellip;</a></p>
{% endif %}

**Bio:** Animesh Trivedi is a tenured Assistant Professor in the Computer Science department at VU Amsterdam. His research interests lie in building fast and efficient systems using modern hardware. He's currently focusing on two emerging research directions. First, how to leverage cheap and fast Flash and Optane NVM storage devices to support demands of data-heavy machine learning workloads. Second, how to design and build foundational software infrastructure and services for the next generation of edge computing applications. Prior to joining VU Amsterdam in 2019, he has worked as a Research Staff Member at the IBM Research Lab in Zürich. He holds a PhD and Master from ETH Zürich. More about his work can be found at [https://animeshtrivedi.github.io](https://animeshtrivedi.github.io).

<!-- 
Animesh Trivedi is a tenure-track Assistant Professor in the department of Computer Science at VU Amsterdam. Prior to joining the department in 2019, he has worked as a Research Staff Member at the IBM Research Lab in Zurich. His research interests lie in building fast and efficient distributed systems around modern high-performance, programmable I/O devices. He is currently investigating how to leverage emerging Non-Volatile Memories (NVMs) to support data access demands of machine learning workloads. He is one of the founding members of the Apache Crail (Incubating) project. He holds a PhD and master from ETH Zurich. More about his work can be found at [https://animeshtrivedi.github.io](https://animeshtrivedi.github.io).-->

### Contact
  * *Email:* a.trivedi AT vu DOT nl 
  * *Phone:* +31 20 598 22 19 
  * *Office:* 11A-33, NU building VU, De Boelelaan 1111, 1081 HV Amsterdam
  * I am also on [Github](https://github.com/animeshtrivedi) and [LinkedIn](https://ch.linkedin.com/in/animesh-trivedi-5407aa2).
