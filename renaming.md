### Renaming Variables

* **names()**

```
> names(leadership)
[1] "age"    "agecat"
> names(leadership)[2] <- "agecategory"
> names(leadership)
[1] "age"         "agecategory"
> names(leadership)[6:10] <- c("item1", "item2", "item3", "item4","item5")
```

* **rename()**

```
> library(plyr)
> leadership <- rename(leadership,c(age="agenew", agecat="agecatnew"))
```