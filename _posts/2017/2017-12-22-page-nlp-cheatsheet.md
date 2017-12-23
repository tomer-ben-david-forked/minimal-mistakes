---
title:  "NLP cheatsheet"
date:   2017-12-22 22:18:00
categories: cheatsheet,NLP
comments: true
permalink: nlp-cheatsheet
---

| Term                    | Meaning                                  |
| ----------------------- | ---------------------------------------- |
| **Weights and Vectors** |                                          |
| TF-IDF                  | Weight higher the more a word appears in doc and not in corpus<br />Term Frequency Inverse Document Frequency |
| length(TF-IDF, doc)     | num of distinct words in doc, for each word number in vector. |
| Word Vectors            | Calculate word vector:<br/>for each word w1 => for each 5 window words, make vectors increasingly<br />closer, v[w1] closer v[w2]<br />king - queen ~ man - woman // wow it will find that for you!<br />You can even download ready made word vectors<br />https://tinyurl.com/word-vectors |
| Google Word Vectors     | You can download ready made google trained vector words |
| **Text Structure**      |                                          |
| Part-Of-Speech Tagging  | word roles: is it verb, noun, …? it's not always obvious |
| Head of sentence        | head(sentence) most important word, it's not nessesaraly the first<br />word, it's the root of the sentence the most important word<br />she hit the wall => hit .<br />You build a graph for a sentence and it becomes the root. |
| Named entities          | People, Companies, Locations, …, quick way to know what text is about. |
| **Sentiment Analysis**  |                                          |
| Sentiment Dictionary    | love +2.9, hated: -3.2, "I loved you but now I hate you" =>  2.9 - 3.2 |
| Sentiment Entities      | Is it about the movie or about the cinema place? |
| Sentiment Features      | Camera/**Resolution** , Camera/**Convinience** |
| **Text Classification** | Decisions, Decisions: What's the Topic, is he happy, native english speaker?<br />Mostly supervised training: We have labels, then map new text to labels |
| Supervised Learning     | We have 3 sets, Train Set, Dev Set, Test Set. |
| Train Set               |                                          |
| Dev(=Validation) Set    | Tuning Parameters (and also to prevent overfitting), tune model |
| Test Set                | Check your model                         |
| Text Features           | Convert documents to be classified into features, <br />bags of words word vectors, can use TF-IDF |
| LDA                     | Latent Dirichlecht Allocation: LDA(Documents) => Topics<br />Technology Topic: Scala, Programming, Machine Learning  <br />Sport Topic: Football, Basketball, Skateboards (3 most important words)<br />Pick number # of topics ahead of time like 5 topics<br />Doc = Distribution(topics) probability for each topic<br />Topic = Distribution(words) technology topic higher probably over cpu word<br />Unsupervised, what topics patterns are there.  Good for getting the sense what the doc is about. |
| **Machine Reading**     |                                          |
| Entity Extraction       | EntityRecognition(text) => (EntityName -> EntityType)<br />("paul newman is a great actor") => [(PaulNewman -> Person)] |
| Entity Linking          | EntityLinking(Entity) => FixedMeaning<br />EntityLinking("PaulNewman") => "http://wikipedia../paul_newman_the_actor"<br />(and not the other paul newman based on text) |
| dbpedia                 | DB for wikipedia, machines can read it its a db.  Query DBPedia with SparQL |
| FRED (lib) / Pikes      | FRED(natural-language) => formal-structure |
| Resources               | <a target="_blank"  href="https://www.amazon.com/gp/product/193398838X/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=193398838X&linkCode=as2&tag=planetizer0c-20&linkId=a3e1a501f6af2cf639f001db0a50f67d"><img border="0" src="//ws-na.amazon-adsystem.com/widgets/q?_encoding=UTF8&MarketPlace=US&ASIN=193398838X&ServiceVersion=20070822&ID=AsinImage&WS=1&Format=_SL250_&tag=planetizer0c-20" ></a><img src="//ir-na.amazon-adsystem.com/e/ir?t=planetizer0c-20&l=am2&o=1&a=193398838X" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> |