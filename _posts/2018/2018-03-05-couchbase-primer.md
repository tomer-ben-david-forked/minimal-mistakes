---
title:  "Couchbase Primer"
date:   2018-03-05 05:18:00
categories: db
permalink: couchbase-primer
comments: true
---

## N1QL

```sql
CREATE PRIMARY INDEX ON  `mybucket`; /* => You have to define a primary index to use n1ql */

SELECT * FROM mybucket;
```