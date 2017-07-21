### Corrective measures

* **Deleting observations**

  * delete outliers
  * delete influential observations

* **Transforming variables**

  * 1/y square, 1/y, 1/sqrt\(y0, log\(y\), sqrt\(y\), y square
  * **powerTransform\(\) : **
    * the result \(0.6\) suggests that you can **normalize **the variable Murder by replacing it with sqrt\(Murder\)
    * But the hypothesis that lambda=1 can't be rejected\(p=0.145\), so there's no strong evidence that a transformation is needed.

* ```
  > summary(powerTransform(states$Murder))
  bcPower Transformation to Normality 
                Est Power Rounded Pwr Wald Lwr bnd Wald Upr Bnd
  states$Murder    0.6055           1       0.0884       1.1227

  Likelihood ratio tests about transformation parameters
                             LRT df       pval
  LR test, lambda = (0) 5.665991  1 0.01729694
  LR test, lambda = (1) 2.122763  1 0.14512456
  ```

  * **boxTidwell\(\)**
    * the result suggests trying the transformations P0.86+I1.35 to achieve greater linearity
    * but the p-values suggest that neither variable needs to be transformed.

```
> boxTidwell(Murder~Population+Illiteracy,data=states)
           Score Statistic   p-value MLE of lambda
Population      -0.3228003 0.7468465     0.8693882
Illiteracy       0.6193814 0.5356651     1.3581188

iterations =  19
```

* **Adding or deleting variables**
* **Trying a different approach**



