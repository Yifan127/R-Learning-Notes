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
![](/ch2-graphs/combining.PNG)

* **layout()**

divide the device into two rows and two columns
allocate figure 1 all of row 1
allocate figure 2 the intersection of column 2 and row 2
the figure in row 1 is twice the height of the figure in row 2
the figure in bottom-right is twice the width of the figure in the bottom-left

**width=lcm(5)**: absolute widths in cm
```
> opar <- par(no.readonly=TRUE)
> layout(matrix(c(1,1,0,2),2,2, byrow=TRUE),widths=c(1,2),height=c(2,1))
> hist(x)
> hist(z)
> par(opar)
```
![](/ch2-graphs/layout.PNG)

* **fig**

fig=c(x1,x2,y1,y2)

```
> opar <- par()
> par(fig=c(0,0.8,0,0.8))
> plot(x,y)
> par(fig=c(0,0.8,0.55,1),new=TRUE)
> boxplot(x,horizontal=TRUE,axes=FALSE)
> par(fig=c(0.65,1,0,0.8),new=TRUE)
> boxplot(y,axes=FALSE)
> mtext("Enhanced Scatterplot", side=3, outer=TRUE, line=-3)
> par(opar)
```
![](/ch2-graphs/fig.PNG)