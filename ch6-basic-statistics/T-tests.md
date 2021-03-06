### T-tests

* **t.test\(y~x\)  **
  * where y is numeric and x is a binary factor
  * var.equal=TRUE : specifies equal variances and a pooled variance estimate.
  * Conclusion is that we reject the null hypothesis that Southern states and non-Southern states have equal probabilities of imprisonment\(p&lt;0.001\)

```
> t.test(Prob~So,data=UScrime,var.equal=TRUE)

    Two Sample t-test

data:  Prob by So
t = -4.2021, df = 45, p-value = 0.0001236
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 -0.03727856 -0.01312153
sample estimates:
mean in group 0 mean in group 1 
     0.03851265      0.06371269
```

* **t.test\(y1,y2\)**
  * where y1 and y2 are numeric
* **t.test\(y1,y2,paired=TRUE\)**
  * where y1 and y2 are numeric

  * the two populations are dependent

  * the conclusion is that we reject the null hypothesis that the mean unemployment rate for older and younger males is the same.

```
> sapply(UScrime[c("U1","U2")],function(x)(c(mean=mean(x),sd=sd(x))))
           U1       U2
mean 95.46809 33.97872
sd   18.02878  8.44545
> with(UScrime,t.test(U1,U2,paired=TRUE))

	Paired t-test

data:  U1 and U2
t = 32.407, df = 46, p-value < 2.2e-16
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 57.67003 65.30870
sample estimates:
mean of the differences 
               61.48936 
```



