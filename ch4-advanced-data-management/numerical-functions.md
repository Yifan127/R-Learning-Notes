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
* **seq()**
```
> seq(1,10,2)
[1] 1 3 5 7 9
```
* **rep()**
```
> rep(1:3,2)
[1] 1 2 3 1 2 3
```
* **pretty()**
```
> pretty(c(-3,3),10)
 [1] -3.0 -2.5 -2.0 -1.5 -1.0 -0.5  0.0  0.5  1.0  1.5  2.0  2.5  3.0
 ```
