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



