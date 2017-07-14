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
* **grep(pattern,x,ignore.case=FALSE,fixed=FALSE)** : 
```
> grep("A",c("b","A","c"),fixed=TRUE)
[1] 2
```
* **sub(pattern,replacement,x,ignore.case=FALSE,fixed=FALSE)**
```
> sub("\\s",".","Hello World")
[1] "Hello.World"
```
* **strsplit(x,split,fixed=FALSE)**
```
> strsplit("abc","")
[[1]]
[1] "a" "b" "c"
```
* **paste()**
```
paste("x",1:3,sep="M")
[1] "xM1" "xM2" "xM3"
```
* **toupper() tolower()**
```
> toupper(x)
[1] "A" "B" "C"
> tolower(x)
[1] "a" "b" "c"
```
