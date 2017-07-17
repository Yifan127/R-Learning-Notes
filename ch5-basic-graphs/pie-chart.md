### Pie chart

* **pie()**
* **pie3D()**
    ```
    > par(mfrow=c(2,2))
    > slices <- c(10,12,4,16,8)
    > lbls <- c("US","UK","Australia","Germany","France")
    > pie(slices,labels = lbls)
    > title("simple pie chart")
    > pct <- round(slices/sum(slices)*100)
    > lbls2 <- paste(lbls, " ", pct, "%", sep="")
    > pie(slices,labels = lbls2,color=rainbow(length(lbls2)),main="pie chart with percentages")
    > library(plotrix)
    
    Attaching package: ¡®plotrix¡¯
    
    The following object is masked from ¡®package:gplots¡¯:
    
        plotCI
    
    > pie3D(slices,labels = lbls, explode = 0.1,main="3D pie chart")
    > mytable <- table(state.region)
    > mytable
    state.region
        Northeast         South North Central          West 
                9            16            12            13 
    > lbls3 <- paste(names(mytable),"\n",mytable,sep="")        
    > pie(mytable,labels = lbls3,main="pie chart from a table\n (with sample sizes)")
    ```
![](/ch5-basic-graphs/pie chart.PNG)   
 