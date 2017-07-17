### Kernel density plot

* **density()**
* **polygon()**
```
> par(mfrow=c(2,1))
> d <- density(mtcars$mpg)
> plot(d)
> plot(d,main="kernel density of miles per gallon")
> polygon(d,col = "red",border = "blue")
> rug(mtcars$mpg,col="brown")
```
![](/ch5-basic-graphs/density.PNG)