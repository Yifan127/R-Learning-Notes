### Selecting models

* **comparing models**
  * anova\(\)
    * compare the fit of two nested models
    * because the test is nonsignificant \(p=0.9939\), the conclusion is that population and illiteracy can be dropped from the model.

```
> fit1 <- lm(Murder~.,data=states)
> fit2 <- lm(Murder~Population+Illiteracy,data=states)
> anova(fit2,fit1)
Analysis of Variance Table

Model 1: Murder ~ Population + Illiteracy
Model 2: Murder ~ Population + Illiteracy + Income + Frost
  Res.Df    RSS Df Sum of Sq      F Pr(>F)
1     47 289.25                           
2     45 289.17  2  0.078505 0.0061 0.9939
```

* * AIC\(\)
    * small value indicates adequate fit with fewer parameters.
    * ANOVA approach requires nested models, but AIC doesn't.

```
> AIC(fit1,fit2)
     df      AIC
fit1  6 241.6429
fit2  4 237.6565
```

* **variable selection**
  * stepwise regression
    * variables are added to or deleted from a model one at a time, until some stopping criterion is reached.
    * forward stepwise: add predictor variables.
    * backward stepwise: start with a model that includes all predictor variables, and then delete them one at a time.
    * not every possible model is evaluated. 

```
> library(MASS)
> fit <- lm(Murder~.,data = states)
> stepAIC(fit,direction = "backward")
Start:  AIC=97.75
Murder ~ Population + Illiteracy + Income + Frost

             Df Sum of Sq    RSS     AIC
- Frost       1     0.021 289.19  95.753
- Income      1     0.057 289.22  95.759
<none>                    289.17  97.749
- Population  1    39.238 328.41 102.111
- Illiteracy  1   144.264 433.43 115.986

Step:  AIC=95.75
Murder ~ Population + Illiteracy + Income

             Df Sum of Sq    RSS     AIC
- Income      1     0.057 289.25  93.763
<none>                    289.19  95.753
- Population  1    43.658 332.85 100.783
- Illiteracy  1   236.196 525.38 123.605

Step:  AIC=93.76
Murder ~ Population + Illiteracy

             Df Sum of Sq    RSS     AIC
<none>                    289.25  93.763
- Population  1    48.517 337.76  99.516
- Illiteracy  1   299.646 588.89 127.311

Call:
lm(formula = Murder ~ Population + Illiteracy, data = states)

Coefficients:
(Intercept)   Population   Illiteracy  
  1.6515497    0.0002242    4.0807366
```

* * all-subsets regression
    * regsubsets\(\)
    * choose R-squared, adjusted R-squared, or Cp statistic as criterion
    * Looking at the 12th row, a model with the intercept, population, illiteracy, and income has an adjusted R-squared of 0.54, whereas one with the intercept, population, and illiteracy alone has a larger adusted R-squared of 0.55. Hence, the two-predictor model is the best.

```
> library(leaps)
> leaps <- regsubsets(Murder~.,data=states,nbest=4)
> plot(leaps,scale = "adjr2")
```

![](/ch7-regression/adjr2.PNG)

```
> subsets(leaps, statistic = "cp",main="cp plot for all subsets regression")
> abline(1,1,lty=2,col="red")
```







