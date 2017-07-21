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



