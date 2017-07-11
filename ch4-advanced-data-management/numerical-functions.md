### Numerical Functions

* **scale()** : standardlizes the specified data to a mean of M and a standard deviation of SD
```
newdata <- scale(mydata) * SD + M
newdata <- transform(mydata, myvar = scale(myvar) * SD + M
)
```
* **runif() and set.seed()**

    * runif() : generates pseudo-random numbers from a uniform distribution on the interval 0 to 1.
    * set.seed() : makes the result reproducible.
```
> runif(5)
[1] 0.6974580 0.3874263 0.9803679 0.6852205 0.9636550
> set.seed(12)
> runif(5)
[1] 0.06936092 0.81777520 0.94262173 0.26938188 0.16934812
> set.seed(12)
> runif(5)
[1] 0.06936092 0.81777520 0.94262173 0.26938188 0.16934812
```