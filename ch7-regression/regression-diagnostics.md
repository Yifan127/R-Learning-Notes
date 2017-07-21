### Regression Diagnostics

* **plot\(fit\)**

```
> fit <- lm(weight~height,data=women)
> par(mfrow=c(2,2))
> plot(fit)
```

* * Normal Q-Q plot: the points on the graph should fall on the straight 45-degree line.
  * Residuals vs Fitted: should not have any special patterns. In the graph, there's a clear evidence of a curved relationship, which suggests that we may want to add a quadratic term to the regression.
  * Scale-Location: the points should be a random band around a horizontal line.![](/ch7-regression/plotfit.PNG)
* **qqPlot\(\)**

  * id.method="identify" makes the plot interactive- clicking on points will add a label.
  * Nevada is an exception, all other points fall close to the line.

```
> library(car)
> qqPlot(fit,labels = row.names(states),id.method = "identify",simulate = TRUE,main="Q-Q Plot")
```

![](/ch7-regression/qqPlot.PNG)

* **Histogram of residuals**

```
> residplot <- function(fit,nbreaks=10){
+ z <- rstudent(fit)
+ hist(z,breaks = nbreaks,freq=FALSE,xlab="Studentized Residual",main = "Distribution of Errors")
+ rug(jitter(z),col="brown")
+ curve(dnorm(x,mean=mean(z),sd=sd(z)),add=TRUE,col="blue",lwd=2)
+ lines(density(z)$x,density(z)$y,col="red",lwd=2,lty=2)
+ legend("topright",legend=c("Normal Curve","Kernel Density Curve"),lty = 1:2,col = c("blue","red"),cex = .7)
+ }
> residplot(fit)
```

![](/ch7-regression/residualplot.PNG)

* **crPlots\(\)** : check the linearity

```
> crPlots(fit)
```

![](/ch7-regression/crplot.PNG)

* **ncvTest\(\)** : check constant variance
  * null hypothesis: constant error variance
  * alternative hypothesis: error variance changes with the level of the fitted values.
  * a significant results suggests nonconstant error variance.

```
> ncvTest(fit)
Non-constant Variance Score Test 
Variance formula: ~ fitted.values 
Chisquare = 1.746514    Df = 1     p = 0.1863156
```

p=0.19, suggesting that you've met the constant variance aussumption.

* **spreadLevelPlot\(\)** : check the constant variance
  * the points should form a random horizontal band around a horizontal line of best fit.
  * the suggested power transformation is the suggested power. 
    * 0.5: sqrt\(y\)
    * 0: log\(y\)
    * 1: no transformation required.

```
> spreadLevelPlot(fit)

Suggested power transformation:  1.209626 
```



