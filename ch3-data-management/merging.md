### Merging

* **merge()** : two data frames are joined by one or more common keys
```
total <- merge(dataframeA, dataframeB, by=c("ID","Country"))
```

* **cbind()** : joins A and B horizontally, and don't need to specify a common key. A and B must have the same number of rows, and be sorted in the same order.
```
total <- cbind(A,B)
```

* **rbind()** : joins A and B vertically. A and B must have the same variables, but don't have to be in the same order.
```
total <- rbind(A,B)
```
    If A has variables that B doesn't:
    * delete extra variables in A
    * create additional variables in B, and set them to NA
