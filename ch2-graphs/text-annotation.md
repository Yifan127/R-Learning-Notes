### Text Annotation

* **text(x,y,"text to place",pos,...)**

    place text within the graph
    **pos**: 1=below, 2=left, 3=above, 4=right
* **mtext("text to place", side, outer=TRUE/FALSE, line=n,...)**: place text in one of the four magines

    **side**: 1=bottom, 2=left, 3=top, 4=right
    **outer**: outer=TRUE, use ouside margin if available
    **line**: on which margin line, starting at 0 counting outwards


```
> opar <- par(no.readonly=TRUE)
> par(cex=1.5)
> plot(1:7,1:7,type="n")
> plot(1:7,1:7,type="b")
> plot(1:7,1:7,type="n")
> text(3,3,"Example of default text")
> text(5,5, family="mono","Example of mono-spaced text")
> text(7,7, family="serif","Example of serif text")
> par(opar)
```

