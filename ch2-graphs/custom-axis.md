### Custom axes

**axis(side,at=,labels=,las=,tck=)**

* **ann=False**: suppress default title and axis labels
* **xaxt="n", yaxt="n"**: suppress x,y axis
* **side**: 1=bottom, 2=left, 3=top, 4=right
* **at**: numeric vector indicating the tick marks
* **las**: specify the label. 0=parallel, 2=perpendicular
* **tck**: length of each tick marks. negative=outside the graph, positive=inside, 0=suppress, 1=create gridlines

```
> x <- c(1:10)
> y <- x
> z <- 10/x
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
![](/ch2-graphs/customaxis.PNG)

* **minor tick marks**

add one minor tick mark between each major tick mark on the xaxis, and two minor tick mark between each major tick mark on the yaxis, and minor tick marks will be 50% as long as the major tick marks. 
```
> library(Hmisc)
> minor.tick(nx=2,ny=3,tick.ratio=0.5)
```
