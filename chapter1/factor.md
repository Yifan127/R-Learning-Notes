### Factor

**Variable Type**
* nominal: categorical without order

Type1, Type2
* ordinal: categorical with order, but not amount

Poor, Improved, Excellent
* continuous: amount with order

11,12,15

**Factor**
nominal and ordinal variables in R are called factors.
**factor(object, order=TRUE/FALSE, levels=c(), labels=c())**
```
> patientID <- c(1,2,3,4)
> diabetes <- c("Type1", "Type2", "Type1", "Type2")
> status <- c("Poor", "Improved", "Excellent", "Poor")
> diabetes <- factor(diabetes)
> diabetes
[1] Type1 Type2 Type1 Type2
Levels: Type1 Type2
> status <- factor(status, order=TRUE)
> status
[1] Poor      Improved  Excellent Poor     
Levels: Excellent < Improved < Poor
> patientdata <- data.frame(patientID, diabetes, status)
> str(patientdata)
'data.frame':   4 obs. of  3 variables:
 $ patientID: num  1 2 3 4
 $ diabetes : Factor w/ 2 levels "Type1","Type2": 1 2 1 2
 $ status   : Ord.factor w/ 3 levels "Excellent"<"Improved"<..: 3 2 1 3
> summary(patientdata)
   patientID     diabetes       status 
 Min.   :1.00   Type1:2   Excellent:1  
 1st Qu.:1.75   Type2:2   Improved :1  
 Median :2.50             Poor     :2  
 Mean   :2.50                          
 3rd Qu.:3.25                          
 Max.   :4.00   
```