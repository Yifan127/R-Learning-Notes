### Violin plot

* **vioplot()**

Violin plot is a combination of a box plot and a kernel density plot.
```
> library(vioplot)
> x1 <- mtcars$mpg[mtcars$cyl==4]
> x2 <- mtcars$mpg[mtcars$cyl==6]
> x3 <- mtcars$mpg[mtcars$cyl==8]
> vioplot(x1,x2,x3,names = c("4 cyl","6 cyl","8 cyl"), col="gold")
> title("violin plot of miles per gallon")
```
![](/ch5-basic-graphs/violinplot.PNG)