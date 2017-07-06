<h3>Data Structure</h3>

* vecter: 1 dimension
```
age <- c(11,21,31)
name <- c(Mary, Mike, Amy)
```
* matrix : 2 dimension
```
matrix(vector, nrow, ncol, byrow, dimnames=list(rnames,cnames))
mymatrix <- matrix(1:6,nrow=2,ncol=3,byrow=TRUE,dimnames=list(c("R1","R2"),c("C1","C2","C3")))
> mymatrix
   C1 C2 C3
R1  1  2  3
R2  4  5  6
```
nrow: number of row
ncol: number of column
byrow: TRUE-filled by row or FALSE-filled by column
rnames,cnames: character vectors stores the row and column labels.
* array: more than 2 dimension
myarray <- array(vector, dimensions, dimnames=list(dim1name, dim2name,dim3name))

**Above three structures can only have one type: numeric, charactor or logical**
* data.frame 




 
