### Array

more than 2 dimensions
array(vector, dimensions, dimnames=list(dim1name, dim2name,dim3name))

**dimensions**: numeric vector giving the max index for each dimension
```
dim1 <- c("A1","A2")
dim2 <- c("B1","B2","B3")
dim3 <- c("C1","C2","C3","C4")
myarray <- array(1:24,c(2,3,4),dimnames=list(dim1,dim2,dim3))
> myarray
, , C1

   B1 B2 B3
A1  1  3  5
A2  2  4  6
, , C2

   B1 B2 B3
A1  7  9 11
A2  8 10 12
, , C3

   B1 B2 B3
A1 13 15 17
A2 14 16 18
, , C4

   B1 B2 B3
A1 19 21 23
A2 20 22 24
```

