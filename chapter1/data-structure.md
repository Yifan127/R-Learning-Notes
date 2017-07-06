<h3>Data Structure</h3>

* **vecter**: 1 dimension
```
age <- c(11,21,31)
name <- c("Mary", "Mike", "Amy")
answer <- c(TRUE,FALSE,TRUE)
> age[1]
[1] 11
> age[c(1,2)]
[1] 11 21
> age[1:3]
[1] 11 21 31
```
* **matrix** : 2 dimension

matrix(vector, nrow, ncol, byrow, dimnames=list(rnames,cnames))

**nrow**: number of row
**ncol**: number of column
**byrow**: TRUE-filled by row or FALSE-filled by column
**rnames,cnames**: character vectors stores the row and column labels.
```
mymatrix <- matrix(1:6,nrow=2,ncol=3,byrow=TRUE,dimnames=list(c("R1","R2"),c("C1","C2","C3")))
> mymatrix
   C1 C2 C3
R1  1  2  3
R2  4  5  6
> mymatrix[2,]
C1 C2 C3 
 4  5  6 
> mymatrix[,2]
R1 R2 
 2  5 
> mymatrix[1,2]
[1] 2
> mymatrix[1,c(2,3)]
C2 C3 
 2  3 
> mymatrix[1,1:2]
C1 C2 
 1  2 

```

* **array**: more than 2 dimension
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

**Above three structures can only have one type: numeric, charactor or logical**
* data frame: Different columns can have different type of data
```
students <- data.frame(name,age,answer)
> students
  name age answer
1 Mary  11   TRUE
2 Mike  21  FALSE
3  Amy  31   TRUE
> students$age
[1] 11 21 31
> students[1:2]
  name age
1 Mary  11
2 Mike  21
3  Amy  31
> students[c(2,3)]
  age answer
1  11   TRUE
2  21  FALSE
3  31   TRUE
```



 
