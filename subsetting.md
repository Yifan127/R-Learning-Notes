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