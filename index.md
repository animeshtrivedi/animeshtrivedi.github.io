---
layout: page
title: About Me
custom_title: Welcome to Animesh Trivedi Homepage
permalink: /
order: 1
---

{% raw %}
<a href="/images/animeshtrivedi-large.jpeg" title="View larger picture"><img src="/images/animeshtrivedi-small.jpeg" alt="Photo of Animesh Trivedi"
style="float:right;width:25%;max-width:200px;margin-left:15px;"/></a>
{% endraw %}

I am **Animesh Trivedi**, a Research Staff Member (RSM) in Cloud and Computing 
Infrastructure group at the IBM Research Lab, Zurich Switzerland. Earlier in 2016, 
I finished my PhD in Computer Science at ETH Zurich under the supervision 
of Prof. Thomas Gross. 
 

My main research areas are networking, operating systems, and distributed 
systems. Broadly speaking, I am interested in the performance aspect of 
systems, spanning from multi-core CPUs to distributed environments. 
In the past, I have designed, developed, and evaluated systems around 
high-performance RDMA networks and NVM storage. Currently, I am 
investigating how modern high-performance devices (think 40-100 Gbps
network, NVMe flash, etc.) can be leveraged in large-scale data 
processing systems such as Spark or Hadoop.
 
<h2>News</h2>
<ul class="news list-unstyled">
{% for post in site.categories.news limit: site.front_page_news %}
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
<p><a href="{{ site.base }}/news/">Older posts&hellip;</a></p>
{% endif %}


## Contact

Email me at: firstname.lastname@alumni.ethz.ch.
I am also on
[Github](https://github.com/animeshtrivedi) and 
[LinkedIn](https://ch.linkedin.com/in/animesh-trivedi-5407aa2).

<br>
<sub>_Website based on the [jekyll-lambda](https://github.com/lauris/lauris.github.com)
theme._</sub>
