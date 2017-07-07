### Graphical Parameters

* **pdf("mustang.pdf")** : outputs the result to pdf file
* **dev.new** createss a new graph window
* **dev.off()** closes current graph window, return the output to screen
* **par()**: produces a list of the current graphical settings
* **par(no.readonly=TRUE)**: produce a list of current graphical settings that can be modified


**Plot**
* **type="b"**: plot both line and points
* **lty**: line type
* **lwd**: line width
* **pch**: point symbol
* **bg**: background color
* **cex**: point symbol size
* **cex.axis**: axis text size
* **font**: specify the font
* **font.axis**: axis text font
* **family**: font family
* **pin**: plot (width, height) in inches.
* **mai**: numeric vector indicating margin size in inches.(bottom, left, top, right)
* **mar**: margin size in lines.
* **main**: title
* **sub**: subtitle
* **xlab, ylab**: axis labels
* **xlim, ylim**: axis ranges

    * Example1:
    ```
    > dose <- c(20,30,40,45,60)
    > drugA <- c(16,20,27,40,60)
    > drugB <- c(15,18,25,31,40)
    > opar <- par(no.readonly=TRUE)
    > par(pin=c(2,3))
    > par(lwd=2,cex=1.5)
    > par(cex.axis=.75,font.axis=3)
    > plot(dose,drugA,type="b",pch=19,lty=2,col="red")
    > plot(dose,drugB,type="b",pch=23,lty=6,col="blue",bg="green")
    > par(opar)
    ```
    * Example2:
    ```
    > plot(dose,drugA,type="b",col="red",lty=2,pch=2,lwd=2, 
    main="Clinical Trials for Drug A", sub="This is hypothetical data",
    xlab="Dosage", ylab="Drug Response", xlim=c(0,60),ylim=c(0,70))
    ```
    
**Color**
* **RColorBrewer**
```
> library(RColorBrewer)
> n <- 7
> mycolors <- brewer.pal(n,"Set1")
> barplot(rep(1,n),col=mycolors)
```
    * brewer.pal.info
    * display.brewer.all()
    
* **Rainbow**
```
> n <-10
> mycolors <- rainbow(n)
> pie(rep(1,n),labels=mycolors,col=mycolors)
```
* **Gray**
```
> n <-10
> mygrays <- gray(0:n/n)
> pie(rep(1,n),labels=mygrays,col=mygrays)
```

**Title**
```
title(main="Clinical Trials for Drug A", col.main="red",sub="This is hypothetical data",
+ col.sub="blue",xlab="my x label", ylab="my y label",col.lab="green",cex.lab=0.75)
```

**Custom axes**
**axis(side,at=,labels=,las=,tck=)**

* **ann=False**: suppress default title and axis labels
* **side**: 1=bottom, 2=left, 3=top, 4=right
* **at**: numeric vector indicating the tick marks
* **las**: specify the label. 0=parallel, 2=perpendicular
* **tck**: length of each tick marks. negative=outside the graph, positive=inside, 0=suppress, 1=create gridlines

```
> opar <- par(no.readonly=TRUE)
> par(mar=c(5,4,4,8)+0.1)
> plot(x,y,type="b",pch=21,col="red",yaxt="n",lty=3,ann=FALSE)
> lines(x,z,type="b",pch=22,col="blue",lty=2)
> axis(2,at=x,labels=x,col.axis="red",las=2)
> axis(4,at=z,labels=round(z,digits=2),col.axis="blue",las=2,cex.axis=0.7,tck=-0.01)
> mtext("y=1/x",side=4,line=3, cex.lab=1,las=2,col="blue")
> title("An Example of Creative Axes", xlab="X values", ylab="Y=X")
> par(opar)
```
* **minor tick marks**

add one minor tick mark between each major tick mark on the xaxis, and two minor tick mark between each major tick mark on the yaxis, and minor tick marks will be 50% as long as the major tick marks. 
```
> library(Hmisc)
> minor.tick(nx=2,ny=3,tick.ratio=0.5)
```
