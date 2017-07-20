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

  * 



