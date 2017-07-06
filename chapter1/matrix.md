### Matrix 

2 dimensions
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

