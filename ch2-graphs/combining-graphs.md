### Combining Graphs

* **mfrow=(nrows,ncols)** : create a matrix of plot, filled by row
* **mfcol=(nrows,ncols)** : create a matrix of plot, filled by column

```
> opar <- par(no.readonly=TRUE)
> par(mfrow=c(2,2))
> plot(x,y,main="Scatterplot of x vs. y")
> plot(x,z,main="Scatterplot of x vs. z")
> hist(x,main="Hisogram of x")
> boxplot(x, main="Boxplot of x")
> par(opar)
```
 