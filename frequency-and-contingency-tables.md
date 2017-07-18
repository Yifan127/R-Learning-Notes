### Frequency and contingency tables

* **One-Way Tables**
  * **table()** : **useNA="ifany"** to include NA as a valid category.
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
* **CrossTable()**
  ```
  > library(gmodels)
  > CrossTable(Arthritis$Treatment,Arthritis$Improved)
  
     Cell Contents
  |-------------------------|
  |                       N |
  | Chi-square contribution |
  |           N / Row Total |
  |           N / Col Total |
  |         N / Table Total |
  |-------------------------|
  
  Total Observations in Table:  84 
  
                      | Arthritis$Improved 
  Arthritis$Treatment |      None |      Some |    Marked | Row Total | 
  --------------------|-----------|-----------|-----------|-----------|
              Placebo |        29 |         7 |         7 |        43 | 
                      |     2.616 |     0.004 |     3.752 |           | 
                      |     0.674 |     0.163 |     0.163 |     0.512 | 
                      |     0.690 |     0.500 |     0.250 |           | 
                      |     0.345 |     0.083 |     0.083 |           | 
  --------------------|-----------|-----------|-----------|-----------|
              Treated |        13 |         7 |        21 |        41 | 
                      |     2.744 |     0.004 |     3.935 |           | 
                      |     0.317 |     0.171 |     0.512 |     0.488 | 
                      |     0.310 |     0.500 |     0.750 |           | 
                      |     0.155 |     0.083 |     0.250 |           | 
  --------------------|-----------|-----------|-----------|-----------|
         Column Total |        42 |        14 |        28 |        84 | 
                      |     0.500 |     0.167 |     0.333 |           | 
  --------------------|-----------|-----------|-----------|-----------|
  ```
* **Multi-dimensional tables**
  * **ftable()**
  ```
  > mytable <- xtabs(~Treatment+Sex+Improved, data=Arthritis)
  > mytable
  , , Improved = None
  
           Sex
  Treatment Female Male
    Placebo     19   10
    Treated      6    7
  
  , , Improved = Some
  
           Sex
  Treatment Female Male
    Placebo      7    0
    Treated      5    2
  
  , , Improved = Marked
  
           Sex
  Treatment Female Male
    Placebo      6    1
    Treated     16    5
  
  > ftable(mytable)
                   Improved None Some Marked
  Treatment Sex                             
  Placebo   Female            19    7      6
            Male              10    0      1
  Treated   Female             6    5     16
            Male               7    2      5
  > margin.table(mytable,1)
  Treatment
  Placebo Treated 
       43      41 
  > margin.table(mytable,2)
  Sex
  Female   Male 
      59     25 
  > margin.table(mytable,3)
  Improved
    None   Some Marked 
      42     14     28 
  > margin.table(mytable,c(1,3))
           Improved
  Treatment None Some Marked
    Placebo   29    7      7
    Treated   13    7     21
  > ftable(prop.table(mytable,c(1,2)))
                   Improved       None       Some     Marked
  Treatment Sex                                             
  Placebo   Female          0.59375000 0.21875000 0.18750000
            Male            0.90909091 0.00000000 0.09090909
  Treated   Female          0.22222222 0.18518519 0.59259259
            Male            0.50000000 0.14285714 0.35714286
  > ftable(addmargins(prop.table(mytable,c(1,2)),3))
                   Improved       None       Some     Marked        Sum
  Treatment Sex                                                        
  Placebo   Female          0.59375000 0.21875000 0.18750000 1.00000000
            Male            0.90909091 0.00000000 0.09090909 1.00000000
  Treated   Female          0.22222222 0.18518519 0.59259259 1.00000000
            Male            0.50000000 0.14285714 0.35714286 1.00000000
  ```