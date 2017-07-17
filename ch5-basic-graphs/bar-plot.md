### Bar plot

* **barplot()**
```
> library(vcd)
> counts <- table(Arthritis$Improved)
> counts

  None   Some Marked 
    42     14     28 
> barplot(counts,main="simple bar plot",xlab="improvement", ylab="frequency")
> barplot(counts,main="simple bar plot",xlab="improvement", ylab="frequency", horiz=TRUE)
```
