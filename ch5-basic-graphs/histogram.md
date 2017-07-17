### Histogram

* **hist()**
* **rug()** : one dimensional representation of the actual data values.
* **jitter() for ties**: add a small random value to each data, in order to avoid overlapping points.

```
> par(mfrow=c(2,2))
> hist(mtcars$mpg)

> hist(mtcars$mpg,breaks = 12,col="red",xlab="Miles per gallon",main="Colored histogram with 12 bins")

> hist(mtcars$mpg,freq=FALSE,breaks = 12,col="red",xlab="Miles per gallon",main="Histogram, rug plot, density curve")
> rug(jitter(mtcars$mpg,amount=0.01))
> lines(density(mtcars$mpg),col="blue",lwd=2)

> x <- mtcars$mpg
> h <- hist(x,breaks = 12,col="red",xlab="Miles per gallon",main="Histogram with normal curve and box")
> xfit <- seq(min(x),max(x),length=40)
> yfit <- dnorm(xfit,mean=mean(x),sd=sd(x))
> yfit <- yfit*diff(h$mids[1:2])*length(x)
> lines(xfit,yfit,col="blue",lwd=2)
> box()
```
![](/ch5-basic-graphs/histogram.PNG)


