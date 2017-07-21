### Unusual observations

* **Outliers**
  * standardized residuals that are larger then 2 or less than -2 are worth attention.

```
> outlierTest(fit)
       rstudent unadjusted p-value Bonferonni p
Nevada 3.542929         0.00095088     0.047544
```

* **High-leverage points**
  * they have an unusal combination of predictor values. The response value isn't involved in determining leverage. For example, Alaska has a much higher income than other states, while having a lower population and temperature.
* * the average hat value:p/n where p: the number of parameters, n is the sample size.
  * an observation with a hat value greater than 2 or 3 times the average hat value should be examined.

```
> hat.plot <- function(fit)
+ {}
> hat.plot <- function(fit){
+ p <- length(coefficients(fit))
+ n <- length(fitted(fit))
+ plot(hatvalues(fit),main = "index plot of hat values")
+ abline(h=c(2,3)*p/n,col="red",lty=2)
+ identify(1:n,hatvalues(fit),names(hatvalues(fit)))
+ }
> hat.plot(fit)
```

![](/ch7-regression/highleverage.PNG)

* **Influential observations**
  * they have a disproportionate impact on the values of the model parameters. The model changes dramatically with the removal of a single observation.
  * Cook's distance, Cook's D values greater than 4/\(n-k-1\), where n is the sample size, k is the number of predictor variables.
  * add variable plot

```
> cutoff <- 4/(nrow(states)-length(coefficients(fit))-2)
> plot(fit,which = 4,cook.levels = cutoff)
> abline(h=cutoff,col="red",lty=2)
```

![](/ch7-regression/cookd.PNG)

```
> avPlots(fit,ask=FALSE,id.method="identify")
```

* **avPlots: assessing the impact of inflential observations**
  * the straight line in each plot is the actual regression coefficient for that predictor variable.
  * for example, look at the graph in the lower-left corner. Eliminating the point labeled Alaska would move the line in a negative direction, which changes the regression coefficient for Income from 0.00006 to -0.00085![](/ch7-regression/avplot.PNG)



