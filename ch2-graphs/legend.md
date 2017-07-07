### Legend

**legend(location,title=,legend,...)**
* **location**: bottomleft, topright...
* **legend**: character vector for labels in legend.

```
> opar <- par(no.readonly=TRUE)
> par(lwd=2,cex=1.5,font.lab=2)
> plot(dose,drugA,type="b",col="red",lty=1,pch=15,ylim=c(0,60),
+ main="Drug A vs. Drug B", xlab="Drug Dosage", ylab="Drug Response")
> lines(dose,drugB,type="b",col="blue",pch=17,lty=2)
> abline(h=c(30),lwd=1.5,lty=2,col="gray")
> library(Hmisc)
> minor.tick(nx=3,ny=3,tick.ratio=0.5)
> legend("topleft",inset=.05,title="Drug Type",c("A","B"),lty=c(1,2),pch=c(15,17),col=c("red","blue"))
> par(opar)
```
![](/ch2-graphs/legend.PNG)
