### Missing Value

* **is.na()** : Test for the presence of missing values.
```
> y <- c(1,2,3,NA)
> is.na(y)
[1] FALSE FALSE FALSE  TRUE
> is.na(leadership[,2])
[1] FALSE FALSE FALSE FALSE FALSE  TRUE
```

* **is.infinite()** : Positvie and negative infinity:Inf() and -Inf()
```
> is.infinite(5/0)
[1] TRUE
```
* **is.nan()** : not a number
```
> is.nan(sin(Inf))
[1] TRUE
```



