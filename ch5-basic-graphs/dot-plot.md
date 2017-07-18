### Dot plot

* **dotchart()**
```
> x <- mtcars[order(mtcars$mpg),]
> x$cyl <- factor(x$cyl)
> x$color[x$cyl==4] <- "red"
> x$color[x$cyl==6] <- "blue"
> x$color[x$cyl==8] <- "darkgreen"
> dotchart(x$mpg,labels = row.names(x),cex = .7,groups = x$cyl,gcolor = "black",color=x$color,pch=19,main="gas mileage for car models\ngrouped by cylinder",xlab="miles per gallon")
```
![](/ch5-basic-graphs/dotchart.PNG)

