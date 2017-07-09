### Sorting

* **order**

```
> attach(leadership)
> newdata <- leadership[order(age),]
> newdata
  manager       date country gender age q1 q2 q3 q4 q5 stringAsFactor
3       3 2008-10-01      UK      F  25  3  5  5  5  2          FALSE
1       1 2008-10-24      US      M  32  5  4  5  5  5          FALSE
4       4 2008-10-12      UK      M  39  3  3  4 NA NA          FALSE
2       2 2008-10-28      US      F  45  3  5  2  5  5          FALSE
5       5 2009-05-01      UK      F  99  2  2  1  2  1          FALSE
> newdata <- leadership[order(gender,age),]
> newdata
  manager       date country gender age q1 q2 q3 q4 q5 stringAsFactor
3       3 2008-10-01      UK      F  25  3  5  5  5  2          FALSE
2       2 2008-10-28      US      F  45  3  5  2  5  5          FALSE
5       5 2009-05-01      UK      F  99  2  2  1  2  1          FALSE
1       1 2008-10-24      US      M  32  5  4  5  5  5          FALSE
4       4 2008-10-12      UK      M  39  3  3  4 NA NA          FALSE
> newdata <- leadership[order(gender,-age),]
> newdata
  manager       date country gender age q1 q2 q3 q4 q5 stringAsFactor
5       5 2009-05-01      UK      F  99  2  2  1  2  1          FALSE
2       2 2008-10-28      US      F  45  3  5  2  5  5          FALSE
3       3 2008-10-01      UK      F  25  3  5  5  5  2          FALSE
4       4 2008-10-12      UK      M  39  3  3  4 NA NA          FALSE
1       1 2008-10-24      US      M  32  5  4  5  5  5          FALSE
> detach(leadership)

```