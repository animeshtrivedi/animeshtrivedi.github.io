---
layout: default
title: "New blog: How to run Crail locally on your laptop"
category: blog
tags: whatsnew
permalink: /run-crail-locally
---

### How to run Crail File System locally using netty 

In this blog post I am going to show how to run Crail file system (CrailFS) 
from [www.crail.io](www.crail.io) ([github](https://github.com/zrlio/crail)) 
locally on your laptop using its netty binding. 

<!-- more -->
First, a bit of background. What is CrailFS? CrailFS is a multi-tiered, 
distributed file system written from scratch to leverage high-performance 
network and storage devices. CrailFS uses RDMA network with NVMeF protocol 
to access remote DRAM and/or flash devices. Using a combination of a clever 
design and a clean implementation, CrailFS can deliver very high performance,
think less than 5 usec latencies with 90+ Gbps bandwidth to data on modern 
high-performance platforms. And this performance can also be translated to 
high application-level performance. I will stop with the introduction here. 
For more curious souls among us, I strongly recommend checking this Spark 
Summit talk at 
[https://spark-summit.org/2017/events/running-apache-spark-on-a-high-performance-cluster-using-rdma-and-nvme-flash/](https://spark-summit.org/2017/events/running-apache-spark-on-a-high-performance-cluster-using-rdma-and-nvme-flash/).
 

Crail is desinged to run on high-end hardware and extract the last 
bit of peformance out of it. But what you do if you just want to test
something? See if works? or Makes sense for you? There are plenty of
reasons that one wishes to just quickly run Crail on the side. But 
not all of us have access to fancy hardware. There are two ways you 
can accomplish this. First, you can use RDMA emulation in software 
using [SoftiWARP](https://github.com/zrlio/softiwarp). 
SoftiWARP is an in-kernel RDMA device, which you can load into 
your kernel and it will make your regular NIC RDMA ready. 
Once you have that, you can follow the rest of the instructions
from the crail website to run crail on RDMA networks. But there 
is a second way as well, which I am going to talk about here. 
Crail has a highly modular architecture, which allows replacing 
communication mechanism by anything that you fancy. And it 
already supports a [netty](https://netty.io/) based transport 
implementation. This is what we are going to use for this blog.


**Step 1: Compiling crail from source**  
  
  * Clone the git repo [https://github.com/zrlio/crail](https://github.com/zrlio/crail)
  
  * Build using a command like 
  
  ```
   $mvn -DskipTests -T 1C  install -Phadoop-2.7
  ```
  
  This tells crail to build for hadoop 2.7 profile (2.6 is also supported). 
  By the end of the build you should have a nice directory in `assembly/target/crail-1.0-bin`.
  This directory contains the build jars, an example configuration, 
  and deployment scripts.

  * Setup a new configuration for your local deployment by renaming and modifying 
  the `conf/crail-site.conf.template` file to `conf/crail-site.conf`. Now, your file must 
  be looking like this at this point:

```text
  crail.blocksize			1048576
  crail.buffersize			1048576
  crail.regionsize			1073741824
  crail.cachelimit			1073741824
  crail.cachepath			<path, should be huge page mountpoint>
  crail.singleton			true
  crail.statistics 			true
  crail.namenode.address	 crail://<hostname>:9060
  crail.namenode.blockselection		roundrobin
  crail.namenode.darpc.queuesize		64
  crail.namenode.darpc.polling		false
  crail.storage.types 			com.ibm.crail.datanode.rdma.RdmaStorageTier
  crail.storage.rdma.interface            eth0
  crail.storage.rdma.port                 50040
  crail.storage.rdma.allocationsize       1073741824
  crail.storage.rdma.storagelimit         10737418240
  crail.storage.rdma.datapath             <path, should be huge page mountpoint>
  crail.storage.rdma.indexpath            <path, cannot be huge page mountpoint>
  crail.storage.rdma.localmap             true
```

In this file you can safely delete all properties concerning `darpc` or `rdma`. 
You should put a mount point, preferably with `hugetlbfs`, but a `tmpfs` 
would do as well. You should modify `crail.namenode.address` to your local 
hostname. And add following entries for the `netty` implementation: 
 
```test
 crail.namenode.rpc.type        com.ibm.crail.namenode.rpc.netty.NettyNameNode
  crail.storage.types com.ibm.crail.storage.netty.NettyStorageTier
 crail.storage.netty.storagelimit       5368709120
 crail.storage.netty.allocationsize     1073741824
 crail.storage.netty.interface          lo
 crail.storage.netty.port               19862
```

Put together, my `conf/crail-site.conf` looks like this: 

```text
crail.blocksize			1048576
crail.buffersize			1048576
crail.regionsize			1073741824
crail.cachelimit			1073741824
crail.cachepath   /tmp/
crail.singleton   true
crail.statistics  true

crail.namenode.address         crail://localhost:9060
crail.namenode.blockselection  roundrobin
crail.namenode.rpc.type        com.ibm.crail.namenode.rpc.netty.NettyNameNode

crail.storage.types com.ibm.crail.storage.netty.NettyStorageTier
crail.storage.netty.storagelimit       5368709120
crail.storage.netty.allocationsize     1073741824
crail.storage.netty.interface          lo
crail.storage.netty.port               19862
```

  * You should also move `conf/core-site.xml.template` to `conf/core-site.xml`. Mine looks like:
      
```text
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!--
  Licensed under the Apache License, Version 2.0 (the "License");
  you may not use this file except in compliance with the License.
  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License. See accompanying LICENSE file.
-->

<!-- Put site-specific property overrides in this file. -->

<configuration>
  <property>
   <name>fs.crail.impl</name>
   <value>com.ibm.crail.hdfs.CrailHadoopFileSystem</value>
  </property>
  <property>
    <name>fs.defaultFS</name>
    <value>crail://localhost:9060</value>
  </property>
  <property>
    <name>fs.AbstractFileSystem.crail.impl</name>
    <value>com.ibm.crail.hdfs.CrailHDFS</value>
  </property>
  <property>
    <name>io.file.buffer.size</name>
    <value>1048576</value>
  </property>
</configuration>
```

**Step 2: Building Crail netty support**  

  * Clone the git repo [https://github.com/zrlio/crail-netty](https://github.com/zrlio/crail-netty)
  
  * Build using `mvn -DskipTests -T 1C  install`
  
  * Then copy two jars namely, `target/crail-netty-1.0.jar` and 
  `target/crail-netty-1.0-dist/jars/netty-all-4.0.29.Final.jar` to Crail's build 
  jar location at `assembly/target/crail-1.0-bin/jars/`. 
  

**Step 3: Running all together**

We we first start the Crail Namenode by hand like:

```text
$./bin/crail namenode
Picked up JAVA_TOOL_OPTIONS:  -XX:+PreserveFramePointer -ea
Java HotSpot(TM) 64-Bit Server VM warning: MaxNewSize (16777216k) is equal to or greater than the entire heap (3960832k).  A new max generation size of 3960320k will be used.
17/07/12 17:34:45 INFO crail: initalizing namenode 
17/07/12 17:34:45 INFO crail: crail.version 2842
17/07/12 17:34:45 INFO crail: crail.storage.types com.ibm.crail.storage.netty.NettyStorageTier
17/07/12 17:34:45 INFO crail: crail.directory.depth 16
17/07/12 17:34:45 INFO crail: crail.token.expiration 10
17/07/12 17:34:45 INFO crail: crail.blocksize 1048576
17/07/12 17:34:45 INFO crail: crail.cachelimit 1073741824
17/07/12 17:34:45 INFO crail: crail.cachepath /tmp/
17/07/12 17:34:45 INFO crail: crail.user stu
17/07/12 17:34:45 INFO crail: crail.shadow.replication 1
17/07/12 17:34:45 INFO crail: crail.debug false
17/07/12 17:34:45 INFO crail: crail.statistics true
17/07/12 17:34:45 INFO crail: crail.rpc.timeout 1000
17/07/12 17:34:45 INFO crail: crail.data.timeout 1000
17/07/12 17:34:45 INFO crail: crail.buffersize 1048576
17/07/12 17:34:45 INFO crail: crail.slicesize 1048576
17/07/12 17:34:45 INFO crail: crail.singleton true
17/07/12 17:34:45 INFO crail: crail.regionsize 1073741824
17/07/12 17:34:45 INFO crail: crail.directoryrecord 512
17/07/12 17:34:45 INFO crail: crail.directoryrandomize true
17/07/12 17:34:45 INFO crail: crail.cacheimpl com.ibm.crail.memory.MappedBufferCache
17/07/12 17:34:45 INFO crail: crail.location.map 
17/07/12 17:34:45 INFO crail: crail.namenode.address crail://localhost:9060
17/07/12 17:34:45 INFO crail: crail.namenode.blockselection roundrobin
17/07/12 17:34:45 INFO crail: crail.namenode.fileblocks 16
17/07/12 17:34:45 INFO crail: crail.namenode.rpc.type com.ibm.crail.namenode.rpc.netty.NettyNameNode
17/07/12 17:34:45 INFO crail: round robin block selection
17/07/12 17:34:45 INFO netty: Starting the NettyNamenode service at : localhost/127.0.0.1:9060

```

Then we start a netty datanode on a second shell as, notice the `-t` flag!

```text
$./bin/crail datanode -t com.ibm.crail.storage.netty.NettyStorageTier 
Picked up JAVA_TOOL_OPTIONS:  -XX:+PreserveFramePointer -ea
Java HotSpot(TM) 64-Bit Server VM warning: MaxNewSize (16777216k) is equal to or greater than the entire heap (3960832k).  A new max generation size of 3960320k will be used.
17/07/12 17:37:14 INFO crail: crail.version 2842
17/07/12 17:37:14 INFO crail: crail.storage.types com.ibm.crail.storage.netty.NettyStorageTier
17/07/12 17:37:14 INFO crail: crail.directory.depth 16
17/07/12 17:37:14 INFO crail: crail.token.expiration 10
17/07/12 17:37:14 INFO crail: crail.blocksize 1048576
17/07/12 17:37:14 INFO crail: crail.cachelimit 1073741824
17/07/12 17:37:14 INFO crail: crail.cachepath /tmp/
17/07/12 17:37:14 INFO crail: crail.user stu
17/07/12 17:37:14 INFO crail: crail.shadow.replication 1
17/07/12 17:37:14 INFO crail: crail.debug false
17/07/12 17:37:14 INFO crail: crail.statistics true
17/07/12 17:37:14 INFO crail: crail.rpc.timeout 1000
17/07/12 17:37:14 INFO crail: crail.data.timeout 1000
17/07/12 17:37:14 INFO crail: crail.buffersize 1048576
17/07/12 17:37:14 INFO crail: crail.slicesize 1048576
17/07/12 17:37:14 INFO crail: crail.singleton true
17/07/12 17:37:14 INFO crail: crail.regionsize 1073741824
17/07/12 17:37:14 INFO crail: crail.directoryrecord 512
17/07/12 17:37:14 INFO crail: crail.directoryrandomize true
17/07/12 17:37:14 INFO crail: crail.cacheimpl com.ibm.crail.memory.MappedBufferCache
17/07/12 17:37:14 INFO crail: crail.location.map 
17/07/12 17:37:14 INFO crail: crail.namenode.address crail://localhost:9060
17/07/12 17:37:14 INFO crail: crail.namenode.blockselection roundrobin
17/07/12 17:37:14 INFO crail: crail.namenode.fileblocks 16
17/07/12 17:37:14 INFO crail: crail.namenode.rpc.type com.ibm.crail.namenode.rpc.netty.NettyNameNode
17/07/12 17:37:14 INFO crail: crail.storage.netty.storagelimit 5368709120
17/07/12 17:37:14 INFO crail: crail.storage.netty.allocationsize 1073741824
17/07/12 17:37:14 INFO crail: crail.storage.netty.interface null
17/07/12 17:37:15 INFO netty: Connected to the Netty Namenode at : localhost/127.0.0.1:9060
17/07/12 17:37:15 INFO crail: connected to namenode at localhost/127.0.0.1:9060
17/07/12 17:37:15 INFO crail: hosthash 111972748
17/07/12 17:37:15 INFO netty: Registering resources with 5 nums of 1073741824 byte buffers
17/07/12 17:37:15 INFO netty: Allocation started for the target of : 5368709120
17/07/12 17:37:15 INFO netty: NettyStorageServer is binded to : 0.0.0.0/0.0.0.0:19862
17/07/12 17:37:15 INFO netty: MAP entry : 7f2787fff000 length : 1073741824 stag : 1 refCount: 2
17/07/12 17:37:15 INFO netty: Allocation done : 20.0% , allocated 1073741824 / 5368709120
17/07/12 17:37:15 INFO netty: MAP entry : 7f2747ffd000 length : 1073741824 stag : 2 refCount: 2
17/07/12 17:37:15 INFO netty: Allocation done : 40.0% , allocated 2147483648 / 5368709120
17/07/12 17:37:16 INFO netty: MAP entry : 7f2707ffb000 length : 1073741824 stag : 3 refCount: 2
17/07/12 17:37:16 INFO netty: Allocation done : 60.0% , allocated 3221225472 / 5368709120
17/07/12 17:37:16 INFO netty: MAP entry : 7f26c7ff9000 length : 1073741824 stag : 4 refCount: 2
17/07/12 17:37:16 INFO netty: Allocation done : 80.0% , allocated 4294967296 / 5368709120
17/07/12 17:37:16 INFO netty: MAP entry : 7f2687ff7000 length : 1073741824 stag : 5 refCount: 2
17/07/12 17:37:16 INFO netty: Allocation done : 100.0% , allocated 5368709120 / 5368709120
17/07/12 17:37:16 INFO crail: datanode statistics, freeBlocks 5120
17/07/12 17:37:18 INFO crail: datanode statistics, freeBlocks 5120
17/07/12 17:37:20 INFO crail: datanode statistics, freeBlocks 5120
17/07/12 17:37:22 INFO crail: datanode statistics, freeBlocks 5120
```
 
and at this point we are good to go ! You can use another shell to use a client like
 

```text
./bin/crail fs -ls /
```


From here on you can interact with the crail file system as you would do with HDFS.  


In a next blog post I will show how to run Spark with Crail.
