### Box plot

* **boxplot()**
```
> boxplot(mtcars$mpg,main="box plot",ylab="miles per gallon")
> boxplot.stats(mtcars$mpg)
$stats
[1] 10.40 15.35 19.20 22.80 33.90
$n
[1] 32
$conf
[1] 17.11916 21.28084
$out
numeric(0)
```
![](/ch5-basic-graphs/box plot.PNG)

* **parallel boxplot**
```
boxplot(mpg~cyl,data=mtcars,main="Car mileage data",xlab="number of cylinders",ylab="miles per gallon")
```
![](/ch5-basic-graphs/parallelboxplot.PNG)
* **notched box plot**

varwidth=TRUE : produces box plots with widths that are proportional to their sample sizes.
```
> boxplot(mpg~cyl,data=mtcars,notch=TRUE,varwidth=TRUE,col="red",main="Car mileage data",xlab="number of cylinders",ylab="miles per gallon")
```
![](/ch5-basic-graphs/notched box plot.PNG)

