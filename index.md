---
layout: default
---
{% raw %}
<a href="/images/2020-atr-image.png" title="View larger picture"><img src="/images/2020-atr-image.png" alt="Photo of Animesh Trivedi"
style="float:right;width:25%;max-width:150px;margin-left:15px;"/></a>
{% endraw %}

<!-- <mark><b>Update:</b></mark> Starting from 2019, I will be joining the Department of Computer Science, VU, Amsterdam as (tenure-track) Assistant Professor. -->

I am an Assistant Professor (tenure-track) at the [CompSys Section](https://www.vucompsys.net/) in the [Department of Computer Science, VU, Amsterdam](https://www.cs.vu.nl/en/index.aspx). 

My main research areas are in storage, networking, operating systems, and distributed systems. Broadly speaking, I am interested in the performance aspect of systems, spanning from multi-core CPUs to distributed systems. Currently, I have following active interests 
  * how to leverage fast and cheap NVM stroage (flash, optane) in data-heavy ML workloads
  * how design and build foundational software services for Edge computing
  * how to design next-generation of systems software for modern, programmable devices

<!-- 
am investigating how modern, programmable, high-performance devices (100+ Gbps network, NVMe/Flash/Optane storage, etc.) can be leveraged in large-scale data-processing and machine learning systems such as Spark, Tensorflow, serverless workloads. 

I am one of the founding contributors of the [Apache Crail (Incubating)](https://crail.incubator.apache.org/) project. Prior to joining VU, I was a Researcher at the IBM Research Lab, Zurich. I obtained my PhD and MSc in Computer Science at ETH Zurich.
Prior to joining VU, I was a Researcher at the IBM Research Lab, Zurich. I obtained my PhD and MSc in Computer Science at ETH Zurich.
finished my PhD in Computer Science at ETH Zurich under the supervision of Prof. Thomas Gross.-->

<mark><b>VU students:</b></mark> If you would like to work on distributed systems (high performance storage, networking) and data-processing frameworks as (a) thesis work; (b) individual research course work; or (c) literature survey work at VU - drop me an email. Also [my advice](/advice/) for working with me.

<!-- <mark><b>TA openings:</b></mark> We have multiple [TA openings](/ta-openings/) in two courses. -->

<!-- <mark><a href="{{ site.base }}/ta-openings/">TA openings</a></mark> --> 

If you are a computer systems researcher in the Netherlands, please consider joining [https://compsys-nl.slack.com/](https://compsys-nl.slack.com/), [[joining link](https://join.slack.com/t/compsys-nl/shared_invite/zt-fx78q58g-Veea9LReM5zA1QqRPQ6peA)].

<!-- 
### Sticky  
  * [<mark>PhD Opening</mark> in the area of NVM storage support for ML](https://workingat.vu.nl/ad/phd-position-in-storage-support-for-machine-learning/w3s7ih), (**deadline: June 15th, 2021**).
  * <mark>CompSys'21 is happening</mark> (June 28th/29th 2021), see [the announcement](/compsys2021-announcement/).
-->
### Sticky  
  * <mark>PhD Opening</mark> in the area of Non-volatile memory storage research, see [here](/21-phd-opening/).

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

**Bio:** Animesh Trivedi is a tenure-track Assistant Professor in the Computer Science department at VU Amsterdam. His research interests lie in building fast and efficient systems using modern hardware. He's currently focusing on two emerging research directions. First, how to leverage cheap and fast Flash and Optane NVM storage devices to support demands of data-heavy machine learning workloads. Second, how to design and build foundational software infrastructure and services for the next generation of edge computing applications. Prior to joining VU Amsterdam in 2019, he has worked as a Research Staff Member at the IBM Research Lab in Zürich. He holds a PhD and Master from ETH Zürich. More about his work can be found at [https://animeshtrivedi.github.io](https://animeshtrivedi.github.io).

<!-- 
Animesh Trivedi is a tenure-track Assistant Professor in the department of Computer Science at VU Amsterdam. Prior to joining the department in 2019, he has worked as a Research Staff Member at the IBM Research Lab in Zurich. His research interests lie in building fast and efficient distributed systems around modern high-performance, programmable I/O devices. He is currently investigating how to leverage emerging Non-Volatile Memories (NVMs) to support data access demands of machine learning workloads. He is one of the founding members of the Apache Crail (Incubating) project. He holds a PhD and master from ETH Zurich. More about his work can be found at [https://animeshtrivedi.github.io](https://animeshtrivedi.github.io).-->

### Contact
  * *Email:* a.trivedi AT vu DOT nl 
  * *Phone:* +31 20 598 22 19 
  * *Office:* 11A-33, NU building VU, De Boelelaan 1111, 1081 HV Amsterdam
  * I am also on [Github](https://github.com/animeshtrivedi) and [LinkedIn](https://ch.linkedin.com/in/animesh-trivedi-5407aa2).
