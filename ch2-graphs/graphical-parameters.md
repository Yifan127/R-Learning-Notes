### Graphical Parameters

* **pdf("mustang.pdf")** : outputs the result to pdf file
* **dev.new** createss a new graph window
* **dev.off()** closes current graph window, return the output to screen
* **par()**: produces a list of the current graphical settings
* **par(no.readonly=TRUE)**: produce a list of current graphical settings that can be modified

```
> dose <- c(20,30,40,45,60)
> drugA <- c(16, 20, 27, 40, 60)
> par(lty=2, pch=17, lwd=2, cex=3)
> plot(dose,drugA,type="b")
> par(opar)
```
**Plot**
* **type="b"**: plot both line and points
* **lty**: line type
* **lwd**: line width
* **pch**: point symbol
* **cex**: point symbol size

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

