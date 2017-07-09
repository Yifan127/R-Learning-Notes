### Variables

* **transform()**
```
> mydata <- data.frame(x1=c(2,2,6,4),x2=c(3,4,2,8))
> mydata <- transform(mydata,sumx=x1+x2,meanx=(x1+x2)/2)
> mydata
  x1 x2 sumx meanx
1  2  3    5   2.5
2  2  4    6   3.0
3  6  2    8   4.0
4  4  8   12   6.0
```