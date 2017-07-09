### Creating Variables

* **variable[condition] `<-` expression**

make the assignment when condition is true

```
> leadership$agecat[leadership$age > 75] <- "Elder"
> leadership$agecat[leadership$age < 55] <- "Young"
> leadership$agecat[leadership$age >= 55 & leadership$age <= 75] <- "Middle Aged"
> leadership
  age agecat
1  32  Young
2  45  Young
3  25  Young
4  39  Young
5  NA   <NA>
```
* **within()**

within() is similar to with(), it allows you to modify the data frame.
First, create variable agecat, and set to NA for each row.
```
> leadership <- within(leadership,{
+ agecat <- NA
+ agecat[age > 75] <- "Elder"
+ agecat[age >= 55 & age <= 75] <- "Middle Aged"
+ agecat[age < 55] <- "Young"
+ agecat[age == 99] <- NA})
```
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
* **Renaming variables**

```
> names(leadership)
[1] "age"    "agecat"
> names(leadership)[2] <- "agecategory"
> names(leadership)
[1] "age"         "agecategory"
> names(leadership)[6:10] <- c("item1", "item2", "item3", "item4","item5")
```