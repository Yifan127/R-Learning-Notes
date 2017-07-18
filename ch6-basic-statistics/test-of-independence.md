### Test of Independence

* **chisq tests**

  * Example1: p`<`0.01, we reject the hypothesis that treatment type and outcome are independent. Therefore, there appears to be a relationship between treatment received and level of improvement.

  ```
  > mytable
           Improved
  Treatment None Some Marked
    Placebo   29    7      7
    Treated   13    7     21
  > chisq.test(mytable)
  
  	Pearson's Chi-squared test
  
  data:  mytable
  X-squared = 13.055, df = 2, p-value = 0.001463
  
  > mytable <- xtabs(~Improved+Sex,data=Arthritis)
  ```
  * Example2: p`<`0.05, we accept the hypothesis that outcome and gender are independent. 
  
  ```
  > mytable
          Sex
  Improved Female Male
    None       25   17
    Some       12    2
    Marked     22    6
  > chisq.test(mytable)
  
  	Pearson's Chi-squared test
  
  data:  mytable
  X-squared = 4.8407, df = 2, p-value = 0.08889
  ```
* **assocstats**

In general, large magnitudes indicate stronger associations.
```
> assocstats(mytable)
                    X^2 df  P(> X^2)
Likelihood Ratio 13.530  2 0.0011536
Pearson          13.055  2 0.0014626

Phi-Coefficient   : NA 
Contingency Coeff.: 0.367 
Cramer's V        : 0.394 
```