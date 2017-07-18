### Descriptive statistics

* **Hmisc describe()**
 ```
 > library(Hmisc)
 > vars <- c("mpg","hp","wt")
 > describe(mtcars[vars])
 mtcars[vars] 
 
  3  Variables      32  Observations
 --------------------------------------------------------------------------------------------------------------------------
 mpg 
        n  missing distinct     Info     Mean      Gmd      .05      .10      .25      .50      .75      .90      .95 
       32        0       25    0.999    20.09    6.796    12.00    14.34    15.43    19.20    22.80    30.09    31.30 
 
 lowest : 10.4 13.3 14.3 14.7 15.0, highest: 26.0 27.3 30.4 32.4 33.9
 --------------------------------------------------------------------------------------------------------------------------
 hp 
        n  missing distinct     Info     Mean      Gmd      .05      .10      .25      .50      .75      .90      .95 
       32        0       22    0.997    146.7    77.04    63.65    66.00    96.50   123.00   180.00   243.50   253.55 
 
 lowest :  52  62  65  66  91, highest: 215 230 245 264 335
 --------------------------------------------------------------------------------------------------------------------------
 wt 
        n  missing distinct     Info     Mean      Gmd      .05      .10      .25      .50      .75      .90      .95 
       32        0       29    0.999    3.217    1.089    1.736    1.956    2.581    3.325    3.610    4.048    5.293 
 
 lowest : 1.513 1.615 1.835 1.935 2.140, highest: 3.845 4.070 5.250 5.345 5.424
 --------------------------------------------------------------------------------------------------------------------------
 ```
* **stat.desc()**
```
> library(pastecs)
> stat.desc(mtcars[vars])
                     mpg           hp          wt
nbr.val       32.0000000   32.0000000  32.0000000
nbr.null       0.0000000    0.0000000   0.0000000
nbr.na         0.0000000    0.0000000   0.0000000
min           10.4000000   52.0000000   1.5130000
max           33.9000000  335.0000000   5.4240000
range         23.5000000  283.0000000   3.9110000
sum          642.9000000 4694.0000000 102.9520000
median        19.2000000  123.0000000   3.3250000
mean          20.0906250  146.6875000   3.2172500
SE.mean        1.0654240   12.1203173   0.1729685
CI.mean.0.95   2.1729465   24.7195501   0.3527715
var           36.3241028 4700.8669355   0.9573790
std.dev        6.0269481   68.5628685   0.9784574
coef.var       0.2999881    0.4674077   0.3041285
```

* **psych describe()**
```
> library(psych)
> describe(mtcars[vars])
    vars  n   mean    sd median trimmed   mad   min    max  range skew kurtosis    se
mpg    1 32  20.09  6.03  19.20   19.70  5.41 10.40  33.90  23.50 0.61    -0.37  1.07
hp     2 32 146.69 68.56 123.00  141.19 77.10 52.00 335.00 283.00 0.73    -0.14 12.12
wt     3 32   3.22  0.98   3.33    3.15  0.77  1.51   5.42   3.91 0.42    -0.02  0.17
```

* **use masked function**
```
> Hmisc::describe(mtcars[vars])
```
* **aggregate()** : only allows single-value functions

 * by=list(am=mtcars$am) : use am as label
 * by=list(mtcars$am) : use Group.1 as label
 ```
 > aggregate(mtcars[vars],by=list(am=mtcars$am),mean)
   am      mpg       hp       wt
 1  0 17.14737 160.2632 3.768895
 2  1 24.39231 126.8462 2.411000
 > aggregate(mtcars[vars],by=list(mtcars$am),sd)
   Group.1      mpg       hp        wt
 1       0 3.833966 53.90820 0.7774001
 2       1 6.166504 84.06232 0.6169816
 ```
* **by()**
 ```
 > mystats <- function(x,na.omit=FALSE){
 + if(na.omit)
 + x <- x[!is.na(x)]
 + m <- mean(x)
 + n <- length(x)
 + s <- sd(x)
 + skew <- sum((x-m)^3/s^3)/n
 + kurt <- sum((x-m)^4/s^4)/n-3
 + return(c(n=n,mean=m,stdev=s,skew=skew,kurtosis=kurt))
 + }
 > dstats <- function(x)sapply(x,mystats)
 > by(mtcars[vars],mtcars$am,dstats)
 mtcars$am: 0
                  mpg           hp         wt
 n        19.00000000  19.00000000 19.0000000
 mean     17.14736842 160.26315789  3.7688947
 stdev     3.83396639  53.90819573  0.7774001
 skew      0.01395038  -0.01422519  0.9759294
 kurtosis -0.80317826  -1.20969733  0.1415676
 ------------------------------------------------------------------------------------------- 
 mtcars$am: 1
                  mpg          hp         wt
 n        13.00000000  13.0000000 13.0000000
 mean     24.39230769 126.8461538  2.4110000
 stdev     6.16650381  84.0623243  0.6169816
 skew      0.05256118   1.3598859  0.2103128
 kurtosis -1.45535200   0.5634635 -1.1737358
 ```
* **summaryBy()**
```
> library(doBy)
> summaryBy(mpg+hp+wt~am,data=mtcars,FUN=mystats)
 am mpg.n mpg.mean mpg.stdev   mpg.skew mpg.kurtosis hp.n  hp.mean hp.stdev     hp.skew hp.kurtosis wt.n  wt.mean
1  0    19 17.14737  3.833966 0.01395038   -0.8031783   19 160.2632 53.90820 -0.01422519  -1.2096973   19 3.768895
2  1    13 24.39231  6.166504 0.05256118   -1.4553520   13 126.8462 84.06232  1.35988586   0.5634635   13 2.411000
  wt.stdev   wt.skew wt.kurtosis
1 0.7774001 0.9759294   0.1415676
2 0.6169816 0.2103128  -1.1737358
```
* **describeBy()**
 ```
 > library(psych)
 > describeBy(mtcars[vars],list(am=mtcars$am))
 
  Descriptive statistics by group 
 am: 0
     vars  n   mean    sd median trimmed   mad   min    max  range  skew kurtosis    se
 mpg    1 19  17.15  3.83  17.30   17.12  3.11 10.40  24.40  14.00  0.01    -0.80  0.88
 hp     2 19 160.26 53.91 175.00  161.06 77.10 62.00 245.00 183.00 -0.01    -1.21 12.37
 wt     3 19   3.77  0.78   3.52    3.75  0.45  2.46   5.42   2.96  0.98     0.14  0.18
 ------------------------------------------------------------------------------------------- 
 am: 1
     vars  n   mean    sd median trimmed   mad   min    max  range skew kurtosis    se
 mpg    1 13  24.39  6.17  22.80   24.38  6.67 15.00  33.90  18.90 0.05    -1.46  1.71
 hp     2 13 126.85 84.06 109.00  114.73 63.75 52.00 335.00 283.00 1.36     0.56 23.31
 wt     3 13   2.41  0.62   2.32    2.39  0.68  1.51   3.57   2.06 0.21    -1.17  0.17
 ```