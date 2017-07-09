### Date Values

* **Default format** : yyyy-mm-dd
```
> mydates <- as.Date(c("2017-01-01","2017-01-02"))
> mydates
[1] "2017-01-01" "2017-01-02"
```
* **as.Date(x,"input_format")** : reads the data using other formats.

    * example1:
    ```
    > strDates <- c("01/05/1965","08/16/1975")
    > dates <- as.Date(strDates, "%m/%d/%Y")
    > dates
    [1] "1965-01-05" "1975-08-16"
    ```
    * example2
    ```
    > myformat <- "%m/%d/%y"
    > leadership$date <- as.Date(leadership$date, myformat)
    > leadership
      manager       date country gender age q1 q2 q3 q4 q5 stringAsFactor
    1       1 2008-10-24      US      M  32  5  4  5  5  5          FALSE
    2       2 2008-10-28      US      F  45  3  5  2  5  5          FALSE
    3       3 2008-10-01      UK      F  25  3  5  5  5  2          FALSE
    4       4 2008-10-12      UK      M  39  3  3  4 NA NA          FALSE
    5       5 2009-05-01      UK      F  99  2  2  1  2  1          FALSE
    ```
* **System Date**
```
> Sys.Date()
[1] "2017-07-09"
> date()
[1] "Sun Jul 09 21:14:53 2017"
```
* **format()**
```
> today <- Sys.Date()
> format(today, format="%B %d %Y")
[1] "July 09 2017"
> format(today, format="%A")
[1] "Sunday"
```
* **difftime**
    * example1:
    ```
    > startdate <- as.Date("2007-03-09")
    > enddate <- as.Date("2017-03-09")
    > days <- enddate-startdate
    > days
    Time difference of 3653 days
    ```   
    * example2:
    units can be seconds, minutes, hours, days, or weeks.
    ```
    > dob <- as.Date("1983-01-27")
    > difftime(today,dob,units="weeks")
    Time difference of 1797.429 weeks
    ```


