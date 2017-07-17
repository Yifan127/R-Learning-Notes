### Bar plot

* **barplot vector**
```
> library(vcd)
> counts <- table(Arthritis$Improved)
> counts

  None   Some Marked 
    42     14     28 
> barplot(counts,main="simple bar plot",xlab="improvement", ylab="frequency")
> barplot(counts,main="simple bar plot",xlab="improvement", ylab="frequency", horiz=TRUE)
```
![](/ch5-basic-graphs/simple bar plot.PNG)
* **barplot matrix**
``` 
> counts <- table(Arthritis$Improved,Arthritis$Treatment)
> counts
        
         Placebo Treated
  None        29      13
  Some         7       7
  Marked       7      21
> barplot(counts,main="stacked bar plot",xlab="treatment", ylab="frequency",col=c("red","yellow","green"),legend=rownames(counts))
> barplot(counts,main="grouped bar plot",xlab="treatment", ylab="frequency",col=c("red","yellow","green"),legend=rownames(counts),beside=TRUE)
```
![](/ch5-basic-graphs/stacked grouped bar plot.PNG)
* **mean barplot**
```
> states <- data.frame(state.region,state.x77)
> means <- aggregate(states$Illiteracy,by=list(state.region),FUN=mean)
> means
        Group.1        x
1     Northeast 1.000000
2         South 1.737500
3 North Central 0.700000
4          West 1.023077
> means <- means[order(means$x),]
> means
        Group.1        x
3 North Central 0.700000
1     Northeast 1.000000
4          West 1.023077
2         South 1.737500
> barplot(means$x,names.arg = means$Group.1)
> title("mean illiteracy rate")
```
![](/ch5-basic-graphs/mean bar plot.PNG)
* **tweaking bar plot**
```
> par(mar=c(5,8,4,2))
> par(las=2)
> counts <- table(Arthritis$Improved)
> barplot(counts,main="treatment outcome",horiz=TRUE,cex.names = 0.8, names.arg = c("no improvement","some improvement","marked improvement"))
```
![](/ch5-basic-graphs/tweaking bar plot.PNG)
* **spinogram**

rescales a stacked bar plot, the height of each bar is 1, and the segment heights represent proportions.
```
> counts <- table(Arthritis$Treatment,Arthritis$Improved)
> spine(counts,main="spinogram example")
```