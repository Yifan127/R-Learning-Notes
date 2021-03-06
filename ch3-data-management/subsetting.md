### Subsetting

* **Excluding variables**
  * Example1:
  ```
  > myvars <- names(leadership) %in% c("q3","q4")
  > myvars
   [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
  > newdata <- leadership[!myvars]
  > newdata
    manager       date country gender age q1 q2 q5 stringAsFactor
  1       1 2008-10-24      US      M  32  5  4  5          FALSE
  2       2 2008-10-28      US      F  45  3  5  5          FALSE
  3       3 2008-10-01      UK      F  25  3  5  2          FALSE
  4       4 2008-10-12      UK      M  39  3  3 NA          FALSE
  5       5 2009-05-01      UK      F  99  2  2  1          FALSE
  ```
  * Example2:
  ```
  > newdata <- leadership[c(-8,-9)]
  > newdata
    manager       date country gender age q1 q2 q5 stringAsFactor
  1       1 2008-10-24      US      M  32  5  4  5          FALSE
  2       2 2008-10-28      US      F  45  3  5  5          FALSE
  3       3 2008-10-01      UK      F  25  3  5  2          FALSE
  4       4 2008-10-12      UK      M  39  3  3 NA          FALSE
  5       5 2009-05-01      UK      F  99  2  2  1          FALSE
  ```
  * Example3:
  ```
  > leadership$q3 <- leadership$q4 <- NULL
  > leadership
    manager       date country gender age q1 q2 q5 stringAsFactor
  1       1 2008-10-24      US      M  32  5  4  5          FALSE
  2       2 2008-10-28      US      F  45  3  5  5          FALSE
  3       3 2008-10-01      UK      F  25  3  5  2          FALSE
  4       4 2008-10-12      UK      M  39  3  3 NA          FALSE
  5       5 2009-05-01      UK      F  99  2  2  1          FALSE
  ```
* **Selecting observations**
```
> newdata <- leadership[leadership$gender == "M" & leadership$age > 30,]
> newdata
  manager       date country gender age q1 q2 q3 q4 q5
1       1 2008-10-24      US      M  32  5  4  5  5  5
4       4 2008-10-12      UK      M  39  3  3  4 NA NA
> startdate <- as.Date("2009-01-01")
> enddate <- as.Date("2009-12-31")
> newdata <- leadership[leadership$date >= startdate & leadership$date <= enddate,]
> newdata
  manager       date country gender age q1 q2 q3 q4 q5
5       5 2009-05-01      UK      F  99  2  2  1  2  1
```

* **subset()**
```
> newdata <- subset(leadership, age >= 35 | age < 24, select=c(q1,q2,q3,q4))
> newdata
  q1 q2 q3 q4
2  3  5  2  5
4  3  3  4 NA
5  2  2  1  2
> newdata <- subset(leadership, gender == "M" | age > 24, select=gender:q4)
> newdata
  gender age q1 q2 q3 q4
1      M  32  5  4  5  5
2      F  45  3  5  2  5
3      F  25  3  5  5  5
4      M  39  3  3  4 NA
5      F  99  2  2  1  2
```

* **sample()**
```
> mysample <- leadership[sample(1:nrow(leadership),3,replace=FALSE),]
> mysample
  manager       date country gender age q1 q2 q3 q4 q5
3       3 2008-10-01      UK      F  25  3  5  5  5  2
4       4 2008-10-12      UK      M  39  3  3  4 NA NA
5       5 2009-05-01      UK      F  99  2  2  1  2  1
```

* **head() and tail()**
```
> head(leadership, n=2)
  manager       date country gender age q1 q2 q3 q4 q5
1       1 2008-10-24      US      M  32  5  4  5  5  5
2       2 2008-10-28      US      F  45  3  5  2  5  5
> tail(leadership, n=2)
  manager       date country gender age q1 q2 q3 q4 q5
4       4 2008-10-12      UK      M  39  3  3  4 NA NA
5       5 2009-05-01      UK      F  99  2  2  1  2  1
```