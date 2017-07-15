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
* **apply(x,MARGIN,FUN)**
 * MARGIN=1: row
 * MARGIN=2: column
 * trim=0.2, discarded the bottom 20% and top 20%
```
> mydata <- matrix(rnorm(30),nrow=6)
> mydata
             [,1]        [,2]        [,3]       [,4]        [,5]
[1,] -0.087160962 -0.33241772 -0.01588746 -1.5416128 -0.74789630
[2,]  1.247023788 -0.28603336 -0.39165024  0.7300144  1.11485661
[3,]  2.334386076  0.48234760 -0.77003247 -0.7587322  0.65502887
[4,]  0.009176622  0.03129139  0.21612574 -0.5013403 -1.63072951
[5,] -0.581954282  0.22435043 -1.26761221 -0.4852918 -0.04625346
[6,]  0.399164723 -0.35495948  1.34466478 -0.4586292 -0.09957550
> apply(mydata,1,mean)
[1] -0.5449950  0.4828422  0.3885996 -0.3750952 -0.4313523  0.1661331
> apply(mydata,2,mean)
[1]  0.55343933 -0.03923686 -0.14739864 -0.50259866 -0.12576155
> apply(mydata,2,mean,trim=0.2)
[1]  0.39205104 -0.09070231 -0.24036111 -0.55099838 -0.05967410
```

 
