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

* **sm.density.compare()**
```
> library(sm)
Package 'sm', version 2.2-5.4: type help(sm) for summary information
> attach(mtcars)
> cyl.f <- factor(cyl,levels = c(4,6,8),labels = c("4 cylinder","6 cylinder","8 cylinder"))
> cyl
 [1] 6 6 4 6 8 6 8 4 4 6 6 8 8 8 8 8 8 4 4 4 4 8 8 8 8 4 4 4 8 6 8 4
> cyl.f
 [1] 6 cylinder 6 cylinder 4 cylinder 6 cylinder 8 cylinder 6 cylinder 8 cylinder 4 cylinder 4 cylinder 6 cylinder
[11] 6 cylinder 8 cylinder 8 cylinder 8 cylinder 8 cylinder 8 cylinder 8 cylinder 4 cylinder 4 cylinder 4 cylinder
[21] 4 cylinder 8 cylinder 8 cylinder 8 cylinder 8 cylinder 4 cylinder 4 cylinder 4 cylinder 8 cylinder 6 cylinder
[31] 8 cylinder 4 cylinder
Levels: 4 cylinder 6 cylinder 8 cylinder
> sm.density.compare(mpg,cyl,xlab="miles per gallon")
> title(main="mgp distribution by car cylinders")
> colfill <- c(2:(1+length(levels(cyl.f))))
> legend(locator(1),levels(cyl.f),fill=colfill)
```
![](/ch5-basic-graphs/densitycompare.PNG)