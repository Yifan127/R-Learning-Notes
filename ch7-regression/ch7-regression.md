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
Multiple R-squared:  0.991,	Adjusted R-squared:  0.9903 
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
  * 

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
Multiple R-squared:  0.9995,	Adjusted R-squared:  0.9994 
F-statistic: 1.139e+04 on 2 and 12 DF,  p-value: < 2.2e-16

> plot(women$height,women$weight,xlab="height",ylab="weight")
> lines(women$height,fitted(fit2))
```



