### Data Frame

Different columns can have different type of data
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
**attach(),detach(),with()**

attach/detach: add/remove the data frame to the R search path. 
summary(age) equals to summary(students$age)
```
> attach(students)
The following objects are masked _by_ .GlobalEnv:

    age, answer, name
> summary(age)  
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
     11      16      21      21      26      31 
> detach(students)
```
**If there is already an object with the same name, the original object takes precedence. Therefore, attach and detach are best used when analyzing a single data frame.**

with: the statements with in {} are evaluated with reference to the students data frame. `<<-` saves the object to the global env outside of the with().

```
> with(students,{
+ nokeep <- summary(age)
+ keep <<- summary(age)
+ })
> nokeep
Error: object 'nokeep' not found
> keep
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
     11      16      21      21      26      31 
```



