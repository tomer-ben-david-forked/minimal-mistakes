---
title:  "NLP cheasheet"
date:   2017-12-17 22:18:00
categories: cheatsheet,NLP
comments: true
permalink: nlp-cheatsheet
---

| Term                   | Meaning                                  |
| ---------------------- | ---------------------------------------- |
| TF-IDF                 | Weight higher the more a word appears in doc and not in corpus |
| length(TF-IDF, doc)    | num of distinct words in doc, for each word number in vector. |
| Word Vectors           | Calculate word vector:<br/>for each word w1 => for each 5 window words, make vectors<br />closer, v[w1] closer v[w2]<br />king - queen ~ man - woman<br />You can even download ready made word vectors<br />https://tinyurl.com/word-vectors |
| Google Word Vectors    | You can download ready made google trained vector words |
| **Text Structure**     |                                          |
| Part-Of-Speech Tagging | word roles: is it verb, noun, …? it's not always obvious |
| Head of sentence       | head(sentence) most important word, it's not nessesaraly the first<br />word, it's the root of the sentence the most important world<br />she hit the wall => hit |


```csv

```


```bash
vectors

word => number # => vector[all words]
doc to vector => 1 in each place word appears in vector[all words] so each doc gets its doc.
better doc to vector => Term Frequency TF vector[#appearances all words]
TF IDF => weight increases the more a word appears in our doc, however, it's offset by the number of times the word appearsin the whole corpus.  https://youtu.be/4vT4fzjkGCQ
TF IDF => is the word special to our doc with regards to the whole corpus.  #term appears in our doc / #times appears in corpus.
IDF => TF * inverse(doc frequency) because rare words are more important for characterizing docs. - 'the' or 'a' will have low rate.
idf(t, D) = log(N / # with t) => t: term freq, # with t: num of docs with term t.
```


Added a printing to current thread:



```scala
      .subscribe(
        x =>
          x match {
            case Nil =>
              logger.trace(s"Got nil from CB getBulkNative textDocs.toList while x is ${x}")
            case _ =>
              logger.info(s"THREAD: ${Thread.currentThread().getName}") // ## PRINT THREAD ##
              x.foreach(singleResp => map.put(singleResp.id, singleResp))
```

Indeed as you said it's using the CB thread pool!

```verilog
2017-12-19 16:57:28,001 INFO  [cb-computations-1] c.t.d.k.InMemCBKeyValueContainer$$anon$1 - THREAD: cb-computations-1 
2017-12-19 16:57:28,129 INFO  [cb-computations-3] c.t.d.k.InMemCBKeyValueContainer$$anon$1 - THREAD: cb-computations-3 
2017-12-19 16:57:28,281 INFO  [cb-computations-1] c.t.d.k.InMemCBKeyValueContainer$$anon$1 - THREAD: cb-computations-1 
2017-12-19 16:57:28,437 INFO  [cb-computations-2] c.t.d.k.InMemCBKeyValueContainer$$anon$1 - THREAD: cb-computations-2 
```

Added this line [.observeOn](http://reactivex.io/documentation/operators/observeon.html)  to the subscribe:

```scala
    textDocs.toList
      .observeOn(ExecutionContextScheduler(scala.concurrent.ExecutionContext.global))
```

Now the output from logs of thread name is of the global execution context thread pool!

```verilog
2017-12-19 17:08:13,472 INFO  [ForkJoinPool-1-worker-5] c.t.d.k.InMemCBKeyValueContainer$$anon$1 - THREAD: ForkJoinPool-1-worker-5 
2017-12-19 17:08:13,606 INFO  [ForkJoinPool-1-worker-5] c.t.d.k.InMemCBKeyValueContainer$$anon$1 - THREAD: ForkJoinPool-1-worker-5 
2017-12-19 17:08:13,752 INFO  [ForkJoinPool-1-worker-1] c.t.d.k.InMemCBKeyValueContainer$$anon$1 - THREAD: ForkJoinPool-1-worker-1 
2017-12-19 17:08:13,909 INFO  [ForkJoinPool-1-worker-1] c.t.d.k.InMemCBKeyValueContainer$$anon$1 - THREAD: ForkJoinPool-1-worker-1 
```

Thanks for igniting me up on the execution context issue to be aware of!!!! ;)