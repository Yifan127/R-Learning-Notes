### Graphical Parameters

* **pdf("mustang.pdf")** : outputs the result to pdf file
* **dev.new** createss a new graph window
* **dev.off()** closes current graph window, return the output to screen
* **par()**: produces a list of the current graphical settings
* **par(no.readonly=TRUE)**: produce a list of current graphical settings that can be modified


**Plot**
* **type="b"**: plot both line and points
* **lty**: line type
* **lwd**: line width
* **pch**: point symbol
* **bg**: background color
* **cex**: point symbol size
* **cex.axis**: axis text size
* **font**: specify the font
* **font.axis**: axis text font
* **family**: font family
* **pin**: plot (width, height) in inches.
* **mai**: numeric vector indicating margin size in inches.(bottom, left, top, right)
* **mar**: margin size in lines.
* **main**: title
* **sub**: subtitle
* **xlab, ylab**: axis labels
* **xlim, ylim**: axis ranges

    * Example1:
    ```
    > dose <- c(20,30,40,45,60)
    > drugA <- c(16,20,27,40,60)
    > drugB <- c(15,18,25,31,40)
    > opar <- par(no.readonly=TRUE)
    > par(pin=c(2,3))
    > par(lwd=2,cex=1.5)
    > par(cex.axis=.75,font.axis=3)
    > plot(dose,drugA,type="b",pch=19,lty=2,col="red")
    > plot(dose,drugB,type="b",pch=23,lty=6,col="blue",bg="green")
    > par(opar)
    ```
    * Example2:
    ```
    > plot(dose,drugA,type="b",col="red",lty=2,pch=2,lwd=2, 
    main="Clinical Trials for Drug A", sub="This is hypothetical data",
    xlab="Dosage", ylab="Drug Response", xlim=c(0,60),ylim=c(0,70))
    ```

    * Example3: **title()**
    ```
    title(main="Clinical Trials for Drug A", col.main="red",sub="This is hypothetical data", col.sub="blue",xlab="my x label", ylab="my y label",col.lab="green",cex.lab=0.75)
    ```
    
    * Example4: **abline()**
    abline(h=yvalue, v=xvalues)



