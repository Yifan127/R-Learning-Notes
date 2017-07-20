### Regression

* **Assumptions**

  * Normality
  * Independence
  * Linearity
  * Constant variance

* **Models**

  * Simple linear regression
  * Polynomial regression
  * Multiple linear regression

* **Simple Linear regression**

  * weight hat = -87.51667+3.45000\*height
  * regression coeffient \(3.45\) is significantly different from zero\(p&lt;0.001\) and indicates that there's an expected increase of 3.45 pounds of weight for every 1 inch increase in height.
  * the multiple R-squared indicates that the model accounts for 99.1% of the variance in weight. It is also the squared correlation between the actual and predicted value.
  * residual standard error \(1.525\) can be thought of as the average error in predicting weight from height using this model.

```
> fit <- lm(weight~height, data=women)
> summary(fit)

Call:
lm(formula = weight ~ height, data = women)

Residuals:
    Min      1Q  Median      3Q     Max 
-1.7333 -1.1333 -0.3833  0.7417  3.1167 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept) -87.51667    5.93694  -14.74 1.71e-09 ***
height        3.45000    0.09114   37.85 1.09e-14 ***
---
Signif. codes:  0 ¡®***¡¯ 0.001 ¡®**¡¯ 0.01 ¡®*¡¯ 0.05 ¡®.¡¯ 0.1 ¡® ¡¯ 1

Residual standard error: 1.525 on 13 degrees of freedom
Multiple R-squared:  0.991,    Adjusted R-squared:  0.9903 
F-statistic:  1433 on 1 and 13 DF,  p-value: 1.091e-14

> fitted(fit)
       1        2        3        4        5        6        7        8        9       10       11       12       13 
112.5833 116.0333 119.4833 122.9333 126.3833 129.8333 133.2833 136.7333 140.1833 143.6333 147.0833 150.5333 153.9833 
      14       15 
157.4333 160.8833 
> residuals(fit)
          1           2           3           4           5           6           7           8           9          10 
 2.41666667  0.96666667  0.51666667  0.06666667 -0.38333333 -0.83333333 -1.28333333 -1.73333333 -1.18333333 -1.63333333 
         11          12          13          14          15 
-1.08333333 -0.53333333  0.01666667  1.56666667  3.11666667 
> plot(women$height,women$weight,xlab="height",ylab="weight")
> abline(fit)
```

* **Polynomial regression**

  * weight hat = 261.87818-7.34832\*height+0.08306\*height^2
  * the amount of variance accounted for has increased to 99.9%

  * the significance of the squared term\(t=13.891,p&lt;0.001\) suggests that the inclusion of the quadratic term improves the model fit.

```
> fit2 <- lm(weight~height+I(height^2),data=women)
> summary(fit2)

Call:
lm(formula = weight ~ height + I(height^2), data = women)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.50941 -0.29611 -0.00941  0.28615  0.59706 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept) 261.87818   25.19677  10.393 2.36e-07 ***
height       -7.34832    0.77769  -9.449 6.58e-07 ***
I(height^2)   0.08306    0.00598  13.891 9.32e-09 ***
---
Signif. codes:  0 ¡®***¡¯ 0.001 ¡®**¡¯ 0.01 ¡®*¡¯ 0.05 ¡®.¡¯ 0.1 ¡® ¡¯ 1

Residual standard error: 0.3841 on 12 degrees of freedom
Multiple R-squared:  0.9995,    Adjusted R-squared:  0.9994 
F-statistic: 1.139e+04 on 2 and 12 DF,  p-value: < 2.2e-16

> plot(women$height,women$weight,xlab="height",ylab="weight")
> lines(women$height,fitted(fit2))
```

* **scatterplot\(\)**
  * scatter plot of weight with height
  * box plots for each variable
  * the linear line of best fit
  * a smoothed fit line \(dashed line\)

```
> library(car)
> scatterplot(weight~height,data=women,spread=FALSE,smoother.args=list(lty=2),pch=19,main="women age 30-39",xlab="height",ylab="weight")
```

![](/ch7-regression/scatterplot.PNG)

* **Examing bivariate relationships**
  * **scatterplotMatrix**
  * murder rate may be bimodal and each of the predictor variables is skewed to some extent
  * murder rates rise with population and illiteracy, and they fall with higher income and frost.
  * colder states have lower illiteracy rates and population and higher incomes.

```
> options(digits = 2)
> cor(states)
           Murder Population Illiteracy Income Frost
Murder       1.00       0.34       0.70  -0.23 -0.54
Population   0.34       1.00       0.11   0.21 -0.33
Illiteracy   0.70       0.11       1.00  -0.44 -0.67
Income      -0.23       0.21      -0.44   1.00  0.23
Frost       -0.54      -0.33      -0.67   0.23  1.00
> scatterplotMatrix(states,spread = FALSE,smoother.args = list(lty=2),main="Scatter plot matrix")
```

![](/ch7-regression/scatterplotmatrix.PNG)

* **Multiple linear regression**
  * the regression coefficient for illiteracy is 4.14, sugguesting that an increase of 1% in illiteracy is associated with a 4.14% increase in the murder rate, controlling for other variables.
  * the coefficient for illiteracy is significantly different from zero at the p&lt;0.0001 level
  * the coefficient for frost isn't significantly different from zero \(p=0.954\), suggesting that frost and murder rate aren't linearly related when controlling for the other variables.
  * the predictor variables account for 56.7% of the variance in murder rates.

```
> fit <- lm(Murder~.,data=states)
> summary(fit)

Call:
lm(formula = Murder ~ ., data = states)

Residuals:
   Min     1Q Median     3Q    Max 
-4.796 -1.649 -0.081  1.482  7.621 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 1.23e+00   3.87e+00    0.32    0.751    
Population  2.24e-04   9.05e-05    2.47    0.017 *  
Illiteracy  4.14e+00   8.74e-01    4.74  2.2e-05 ***
Income      6.44e-05   6.84e-04    0.09    0.925    
Frost       5.81e-04   1.01e-02    0.06    0.954    
---
Signif. codes:  0 ¡®***¡¯ 0.001 ¡®**¡¯ 0.01 ¡®*¡¯ 0.05 ¡®.¡¯ 0.1 ¡® ¡¯ 1

Residual standard error: 2.5 on 45 degrees of freedom
Multiple R-squared:  0.567,	Adjusted R-squared:  0.528 
F-statistic: 14.7 on 4 and 45 DF,  p-value: 9.13e-08
```



