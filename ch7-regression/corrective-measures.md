### Corrective measures

* **Deleting observations**

  * delete outliers
  * delete influential observations

* **Transforming variables**

  * 1/y square, 1/y, 1/sqrt\(y0, log\(y\), sqrt\(y\), y square
  * **powerTransform\(\)**
    * the result \(0.6\) suggests that you can replace Murder with sqrt\(Murder\)
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





