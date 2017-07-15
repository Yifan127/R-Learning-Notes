### Aggregation and reshaping

* **t()**: transpose a matrix or a data frame. (reversing rows and columns)
```
> cars <- mtcars[1:5,1:4]
> cars
                  mpg cyl disp  hp
Mazda RX4          21   6  160 110
Mazda RX4 Wag      21   6  160 110
Datsun 710         23   4  108  93
Hornet 4 Drive     21   6  258 110
Hornet Sportabout  19   8  360 175
> t(cars)
     Mazda RX4 Mazda RX4 Wag Datsun 710 Hornet 4 Drive Hornet Sportabout
mpg         21            21         23             21                19
cyl          6             6          4              6                 8
disp       160           160        108            258               360
hp         110           110         93            110               175
```