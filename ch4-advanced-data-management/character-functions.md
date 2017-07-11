### Character Functions

* **nchar()** : counts the number of characters of x.
```
> x <- c("ab","cde","fghi")
> length(x)
[1] 3
> nchar(x[3])
[1] 4
```
* **substr()** : extracts or replace substrings
```
> substr(x[3],2,4)
[1] "ghi"
> substr(x[3],2,4) <- "222"
> x
[1] "ab"   "cde"  "f222"
```