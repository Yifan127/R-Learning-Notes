### Frequency and contingency tables

* **One-Way Tables**
  * **table()**
  * **prop.table()**
  ```
  > library(vcd)
  > head(Arthritis)
    ID Treatment  Sex Age Improved
  1 57   Treated Male  27     Some
  2 46   Treated Male  29     None
  3 77   Treated Male  30     None
  4 17   Treated Male  32   Marked
  5 36   Treated Male  46   Marked
  6 23   Treated Male  58   Marked
  > mytable <- with(Arthritis,table(Improved))
  > mytable
  Improved
    None   Some Marked 
      42     14     28 
  > prop.table(mytable)
  Improved
       None      Some    Marked 
  0.5000000 0.1666667 0.3333333 
  > prop.table(mytable)*100
  Improved
      None     Some   Marked 
  50.00000 16.66667 33.33333 
  ```
* **Two-Way Table: xtabs()**
  * **xtabs()**
  * **margins.table()**
  * **addmargins()**
```
> mytable <- xtabs(~Treatment+Improved,data=Arthritis)
> mytable
         Improved
Treatment None Some Marked
  Placebo   29    7      7
  Treated   13    7     21
> margin.table(mytable,1)
Treatment
Placebo Treated 
     43      41 
> prop.table(mytable,1)
         Improved
Treatment      None      Some    Marked
  Placebo 0.6744186 0.1627907 0.1627907
  Treated 0.3170732 0.1707317 0.5121951
> margin.table(mytable,2)
Improved
  None   Some Marked 
    42     14     28 
> prop.table(mytable,2)
         Improved
Treatment      None      Some    Marked
  Placebo 0.6904762 0.5000000 0.2500000
  Treated 0.3095238 0.5000000 0.7500000
> addmargins(mytable)
         Improved
Treatment None Some Marked Sum
  Placebo   29    7      7  43
  Treated   13    7     21  41
  Sum       42   14     28  84
> addmargins(prop.table(mytable))
         Improved
Treatment       None       Some     Marked        Sum
  Placebo 0.34523810 0.08333333 0.08333333 0.51190476
  Treated 0.15476190 0.08333333 0.25000000 0.48809524
  Sum     0.50000000 0.16666667 0.33333333 1.00000000
> addmargins(prop.table(mytable,1),2)
         Improved
Treatment      None      Some    Marked       Sum
  Placebo 0.6744186 0.1627907 0.1627907 1.0000000
  Treated 0.3170732 0.1707317 0.5121951 1.0000000
> addmargins(prop.table(mytable,2),1)
         Improved
Treatment      None      Some    Marked
  Placebo 0.6904762 0.5000000 0.2500000
  Treated 0.3095238 0.5000000 0.7500000
  Sum     1.0000000 1.0000000 1.0000000
```