### Missing Value

* **is.na()** : Test for the presence of missing values.
```
> y <- c(1,2,3,NA)
> is.na(y)
[1] FALSE FALSE FALSE  TRUE
> is.na(leadership[,2])
[1] FALSE FALSE FALSE FALSE FALSE  TRUE
```

* **is.infinite()** : Positvie and negative infinity:Inf() and -Inf()
```
> is.infinite(5/0)
[1] TRUE
```
* **is.nan()** : not a number
```
> is.nan(sin(Inf))
[1] TRUE
```

* **na.rm=TRUE** : excluding missing values
```
> x <- c(1,2,NA,3)
> y <- sum(x)
> y
[1] NA
> y <- sum(x,na.rm=TRUE)
> y
[1] 6
```

* **na.omit()** : deletes any rows with missing data
```
> leadership
  manager     date country gender age q1 q2 q3 q4 q5 stringAsFactor
1       1 10/24/08      US      M  32  5  4  5  5  5          FALSE
2       2 10/28/08      US      F  45  3  5  2  5  5          FALSE
3       3  10/1/08      UK      F  25  3  5  5  5  2          FALSE
4       4 10/12/08      UK      M  39  3  3  4 NA NA          FALSE
5       5   5/1/09      UK      F  99  2  2  1  2  1          FALSE
> newdata <- na.omit(leadership)
> newdata
  manager     date country gender age q1 q2 q3 q4 q5 stringAsFactor
1       1 10/24/08      US      M  32  5  4  5  5  5          FALSE
2       2 10/28/08      US      F  45  3  5  2  5  5          FALSE
3       3  10/1/08      UK      F  25  3  5  5  5  2          FALSE
5       5   5/1/09      UK      F  99  2  2  1  2  1          FALSE
```



