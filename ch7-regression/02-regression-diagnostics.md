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

![](/ch7-regression/spreadlevelplot.PNG)

* **gvlma\(\)**
  * p=0.5965 indicates that the data meet all the assumptions that go with the model.
  * if say p&lt;0.05, the assumptions are violated, then you'd have to explore the data using above methods.

```
> library(gvlma)
> gvmodel <- gvlma(fit)
> summary(gvmodel)

Call:
lm(formula = Murder ~ ., data = states)

Residuals:
    Min      1Q  Median      3Q     Max 
-4.7960 -1.6495 -0.0811  1.4815  7.6210 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept) 1.235e+00  3.866e+00   0.319   0.7510    
Population  2.237e-04  9.052e-05   2.471   0.0173 *  
Illiteracy  4.143e+00  8.744e-01   4.738 2.19e-05 ***
Income      6.442e-05  6.837e-04   0.094   0.9253    
Frost       5.813e-04  1.005e-02   0.058   0.9541    
---
Signif. codes:  0 ¡®***¡¯ 0.001 ¡®**¡¯ 0.01 ¡®*¡¯ 0.05 ¡®.¡¯ 0.1 ¡® ¡¯ 1

Residual standard error: 2.535 on 45 degrees of freedom
Multiple R-squared:  0.567,	Adjusted R-squared:  0.5285 
F-statistic: 14.73 on 4 and 45 DF,  p-value: 9.133e-08


ASSESSMENT OF THE LINEAR MODEL ASSUMPTIONS
USING THE GLOBAL TEST ON 4 DEGREES-OF-FREEDOM:
Level of Significance =  0.05 

Call:
 gvlma(x = fit) 

                    Value p-value                Decision
Global Stat        2.7728  0.5965 Assumptions acceptable.
Skewness           1.5374  0.2150 Assumptions acceptable.
Kurtosis           0.6376  0.4246 Assumptions acceptable.
Link Function      0.1154  0.7341 Assumptions acceptable.
Heteroscedasticity 0.4824  0.4873 Assumptions acceptable.
```

* **vif\(\) : **check multicollinearity
  * if sqrt\(vif\)&gt;2, it indicates a multicollinearity problem.

```
> vif(fit)
Population Illiteracy     Income      Frost 
  1.245282   2.165848   1.345822   2.082547 
> sqrt(vif(fit))
Population Illiteracy     Income      Frost 
  1.115922   1.471682   1.160096   1.443103 
> sqrt(vif(fit)) > 2
Population Illiteracy     Income      Frost 
     FALSE      FALSE      FALSE      FALSE 
```



