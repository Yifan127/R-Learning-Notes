### Data Input

* **edit()**

```
mydata <- data.frame(age=numeric(0),gender=character(0),weight=numeric(0))
mydata <- edit(mydata)
fix(mydata)
```

* **read.table()**

```
mydata <- read.table("D:/Rspace/project1/transaction.csv", header=FALSE, sep="\t")
```
**row.names="patientID"**: specify row identifiers.
    
read.table() converts character variables to factors, to suppress this behavior:

    * add this option **stringAsFactors=FALSE**
    * or specify a class for each column **colClasses=c("charactre","numeric")**



