### List

**list** gathers a variety of objects under one name.
```
> mylist <- list(title="my list", ages=age, mymatrix, name)
> mylist
$title
[1] "my list"

$ages
[1] 11 21 31

[[3]]
   C1 C2 C3
R1  1  2  3
R2  4  5  6

[[4]]
[1] "Mary" "Mike" "Amy" 

> mylist[[2]]
[1] 11 21 31
> mylist$ages
[1] 11 21 31
> mylist[["ages"]]
[1] 11 21 31
```