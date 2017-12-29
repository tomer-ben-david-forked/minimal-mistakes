---
title:  "Data Science cheatsheet"
date:   2017-12-22 22:18:00
categories: cheatsheet,NLP
comments: true
permalink: datascience-cheatsheet
---

| Topic                     | HOWTO                                    |
| ------------------------- | ---------------------------------------- |
| **Study Resources**       |                                          |
| General Big Data          | <a target="_blank"  href="https://www.amazon.com/gp/product/1946383481/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1946383481&linkCode=as2&tag=planetizer0c-20&linkId=58766618ae5432f218a7c8db17c0d4e5"><img border="0" src="//ws-na.amazon-adsystem.com/widgets/q?_encoding=UTF8&MarketPlace=US&ASIN=1946383481&ServiceVersion=20070822&ID=AsinImage&WS=1&Format=_SL250_&tag=planetizer0c-20" ></a><img src="//ir-na.amazon-adsystem.com/e/ir?t=planetizer0c-20&l=am2&o=1&a=1946383481" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> |
| Apache Spark              | <a target="_blank"  href="https://www.amazon.com/gp/product/0672338513/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0672338513&linkCode=as2&tag=planetizer0c-20&linkId=9e3d739aad73dc61faee301221c4a8b9"><img border="0" src="//ws-na.amazon-adsystem.com/widgets/q?_encoding=UTF8&MarketPlace=US&ASIN=0672338513&ServiceVersion=20070822&ID=AsinImage&WS=1&Format=_SL250_&tag=planetizer0c-20" ></a><img src="//ir-na.amazon-adsystem.com/e/ir?t=planetizer0c-20&l=am2&o=1&a=0672338513" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> |
| Amazon EMR                | https://aws.amazon.com/emr/getting-started/ |
| Data Science RND Workflow | https://alexioannides.com/2016/08/16/building-a-data-science-platform-for-rd-part-1-setting-up-aws/ |

## Apache Spark

| **Spark Term**             | **Description**                          |
| -------------------------- | ---------------------------------------- |
| **Spark Architecture**     | ![spark-architecture-diagram](https://spark.apache.org/docs/latest/img/cluster-overview.png) |
| Spark Driver               | sends work like 1                        |
| Spark Worker               | like multiple of them, we want enough RAM memory connecting to hdfs |
| RDD                        | Distributed collection with api, immutable, fault tolerant |
| Partition > Executors      | * Optimize: At least many partitions (shard) to data like num of executors<br />* So that each executor can work in parallel on some partition of the data |
| Immutability               | FirstRDD points to SecondRDD points to ThirdRDD (transformations) |
| Fault Tolerance            | If spark-worker fails work restarts on another spark-worker by spark-driver |
| Partitioning               | Data is broken into partitions 3         |
| Worker node 1* Executor    |                                          |
| Transformations VS Actions | * Transformations [Lazy]: map, flatMap, filter, groupBy, mapValues, ...<br />* Actions: take, count, collect, reduce, top |
| **Skeleton Project**       |                                          |
| dependency                 | * "org.apache.spark" %% "spark-core"<br />* create fatJar in assembly |
| **Use Spark**              |                                          |
| create SparkContext        | * `val sparkConf = new SparkConf().setAppName("somename").set("spark.io.compress.codec", "lzf")` <br />* `val sc = new SparkContext(conf)` |
| submit it                  | `spark-submit com.mypackage.MySparkApp —master local[*] my-fat-jar-without-spark.jar` <br />// spark-submit is part of spark we downloaded<br />// [*] use cpu cores as many as you have<br />// To deploy to cluster you are going to have [many more params](https://spark.apache.org/docs/latest/submitting-applications.html) |
| **Spark API**              |                                          |
| `spark-shell`              | Explore the api with spark shell, already has spark context `sc` |
| `sc.makeRDD(List(1,2))`    |                                          |
| `rdd.map`                  | `val myRdd = rdd.map(_ * 2)` // returns RDD |
| `myRdd.collect()`          | `Array(2,4)`                             |
| `rdd.cache()`              | So that if you have multiple `.action()` like `.collect()` data won't be referched for the transformations rdd again. |
| **NLP Spark**              |                                          |
| Clean Text                 | tokenize, remove whitespaces, filter empty strings, wors to lower case |
| sc.textFile                | `sc.textFile("/folder/book1.txt,/folder/book2.txt")` |
| partitions                 | `sc.textFile("/folder/book1.txt,/folder/book2.txt", 5)` // split to 5 partitions!! so now we can utilize 5 workers. |

