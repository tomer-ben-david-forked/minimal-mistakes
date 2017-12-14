---

title:  "R cheasheet"
date:   2017-12-12 22:18:00
categories: cheatsheet,R
comments: true
permalink: r-cheatsheet
---
**Read log file and print line chart**

```r
df = read.table("~/tmp/heapmem.log", header = FALSE)
matplot(df$V4, type="l")
```

in column 4 we have the heapmem it will produce the linechart.

**Getting help and examples**

```r
help(read.table)
example(read.table)
vignettes() # PDF documentation on a topic.
vignettes(package = .packages(all.available = TRUE)) # include more non standard topics.
```

## Plotting

diamond data source

```
  carat       cut color clarity depth table price     x     y
  <dbl>     <ord> <ord>   <ord> <dbl> <dbl> <int> <dbl> <dbl>
1  0.23     Ideal     E     SI2  61.5    55   326  3.95  3.98
2  0.21   Premium     E     SI1  59.8    61   326  3.89  3.84
3  0.23      Good     E     VS1  56.9    65   327  4.05  4.07
```

plot the proportion of cut (without ..prop.. would simply count it)

```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, y = ..prop.., group = 1))
```

## Log file analysis

install.packages("devtools")
library(devtools
install_github("kevinushey/rex")
library(rex)

http://www.mjdenny.com/Text_Processing_In_R.html

`diy <- grep("getAllForType.multithreaded", readLines("~/Downloads/diy-play-fail-log.html"), value = TRUE)`

