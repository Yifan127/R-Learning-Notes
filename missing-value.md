### Missing Value

* **is.na()**
test for the presence of missing values.

```
> y <- c(1,2,3,NA)
> is.na(y)
[1] FALSE FALSE FALSE  TRUE
> is.na(leadership[,2])
[1] FALSE FALSE FALSE FALSE FALSE  TRUE
```
