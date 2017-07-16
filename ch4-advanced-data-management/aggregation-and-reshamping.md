### Aggregation and reshaping

* **t()**: transpose a matrix or a data frame. (reversing rows and columns)
```
> cars <- mtcars[1:5,1:4]
> cars
                  mpg cyl disp  hp
Mazda RX4          21   6  160 110
Mazda RX4 Wag      21   6  160 110
Datsun 710         23   4  108  93
Hornet 4 Drive     21   6  258 110
Hornet Sportabout  19   8  360 175
> t(cars)
     Mazda RX4 Mazda RX4 Wag Datsun 710 Hornet 4 Drive Hornet Sportabout
mpg         21            21         23             21                19
cyl          6             6          4              6                 8
disp       160           160        108            258               360
hp         110           110         93            110               175
```
* **aggregate(x,by=list(),FUN)**

  For example, cars with 4 cylinders and 3 gears have a mean of 21.5 miles per gallon.
  ```
  > options(digits=3)
  > attach(mtcars)
  > aggdata <- aggregate(mtcars, by=list(cyl,gear), FUN=mean, na.rm=TRUE)
  > aggdata
    Group.1 Group.2  mpg cyl disp  hp drat   wt qsec  vs   am gear carb
  1       4       3 21.5   4  120  97 3.70 2.46 20.0 1.0 0.00    3 1.00
  2       6       3 19.8   6  242 108 2.92 3.34 19.8 1.0 0.00    3 1.00
  3       8       3 15.1   8  358 194 3.12 4.10 17.1 0.0 0.00    3 3.08
  4       4       4 26.9   4  103  76 4.11 2.38 19.6 1.0 0.75    4 1.50
  5       6       4 19.8   6  164 116 3.91 3.09 17.7 0.5 0.50    4 4.00
  6       4       5 28.2   4  108 102 4.10 1.83 16.8 0.5 1.00    5 2.00
  7       6       5 19.7   6  145 175 3.62 2.77 15.5 0.0 1.00    5 6.00
  8       8       5 15.4   8  326 300 3.88 3.37 14.6 0.0 1.00    5 6.00
  ```
* **melt(data,id=c())**
```
> library(reshape2)
> ID <- c(1,1,2,2)
> Time <- c(1,2,1,2)
> X1 <- c(5,3,6,2)
> X2 <- c(6,5,1,4)
> mydata <- data.frame(ID,Time,X1,X2)
> mydata
  ID Time X1 X2
1  1    1  5  6
2  1    2  3  5
3  2    1  6  1
4  2    2  2  4
> md <- melt(mydata,id=c("ID","Time"))
> md
  ID Time variable value
1  1    1       X1     5
2  1    2       X1     3
3  2    1       X1     6
4  2    2       X1     2
5  1    1       X2     6
6  1    2       X2     5
7  2    1       X2     1
8  2    2       X2     4
```
* **dcast()**
```
> newdata <- dcast(md,ID~variable,mean)
> newdata
  ID X1  X2
1  1  4 5.5
2  2  4 2.5
> newdata <- dcast(md,Time~variable,mean)
> newdata
  Time  X1  X2
1    1 5.5 3.5
2    2 2.5 4.5
> newdata <- dcast(md,ID~Time,mean)
> newdata
  ID   1 2
1  1 5.5 4
2  2 3.5 3
> newdata <- dcast(md,ID+Time~variable,mean)
> newdata
  ID Time X1 X2
1  1    1  5  6
2  1    2  3  5
3  2    1  6  1
4  2    2  2  4
> newdata <- dcast(md,ID+variable~Time,mean)
> newdata
  ID variable 1 2
1  1       X1 5 3
2  1       X2 6 5
3  2       X1 6 2
4  2       X2 1 4
> newdata <- dcast(md,ID~variable+Time,mean)
> newdata
  ID X1_1 X1_2 X2_1 X2_2
1  1    5    3    6    5
2  2    6    2    1    4
```
