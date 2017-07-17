### Bar plot

* **barplot()**
  * Example1: plot vector
  ```
  > library(vcd)
  > counts <- table(Arthritis$Improved)
  > counts
  
    None   Some Marked 
      42     14     28 
  > barplot(counts,main="simple bar plot",xlab="improvement", ylab="frequency")
  > barplot(counts,main="simple bar plot",xlab="improvement", ylab="frequency", horiz=TRUE)
  ```
  ![](/assets/simple bar chart.PNG)
  * Example2: plot matrix
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
  ![](/assets/stacked grouped bar plot.PNG)
