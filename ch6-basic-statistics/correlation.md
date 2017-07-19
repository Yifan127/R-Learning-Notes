### Correlations

* **cov\(\)**

```
> states <- state.x77[,1:6]
> head(states)
           Population Income Illiteracy Life Exp Murder HS Grad
Alabama          3615   3624        2.1    69.05   15.1    41.3
Alaska            365   6315        1.5    69.31   11.3    66.7
Arizona          2212   4530        1.8    70.55    7.8    58.1
Arkansas         2110   3378        1.9    70.66   10.1    39.9
California      21198   5114        1.1    71.71   10.3    62.6
Colorado         2541   4884        0.7    72.06    6.8    63.9
> cov(states)
              Population      Income   Illiteracy     Life Exp      Murder      HS Grad
Population 19931683.7588 571229.7796  292.8679592 -407.8424612 5663.523714 -3551.509551
Income       571229.7796 377573.3061 -163.7020408  280.6631837 -521.894286  3076.768980
Illiteracy      292.8680   -163.7020    0.3715306   -0.4815122    1.581776    -3.235469
Life Exp       -407.8425    280.6632   -0.4815122    1.8020204   -3.869480     6.312685
Murder         5663.5237   -521.8943    1.5817755   -3.8694804   13.627465   -14.549616
HS Grad       -3551.5096   3076.7690   -3.2354694    6.3126849  -14.549616    65.237894
```

* **cor\(\)**
  * there's a strong positive correlation exists between income and high school graduation.
  * there's a strong negative correlation exists between illiteracy rates and life expectancy.

```
> cor(states)
            Population     Income Illiteracy    Life Exp     Murder     HS Grad
Population  1.00000000  0.2082276  0.1076224 -0.06805195  0.3436428 -0.09848975
Income      0.20822756  1.0000000 -0.4370752  0.34025534 -0.2300776  0.61993232
Illiteracy  0.10762237 -0.4370752  1.0000000 -0.58847793  0.7029752 -0.65718861
Life Exp   -0.06805195  0.3402553 -0.5884779  1.00000000 -0.7808458  0.58221620
Murder      0.34364275 -0.2300776  0.7029752 -0.78084575  1.0000000 -0.48797102
HS Grad    -0.09848975  0.6199323 -0.6571886  0.58221620 -0.4879710  1.00000000
```

```
> x <- states[,c("Population","Income","Illiteracy","HS Grad")]
> y <- states[,c("Life Exp","Murder")]
> cor(x,y)
              Life Exp     Murder
Population -0.06805195  0.3436428
Income      0.34025534 -0.2300776
Illiteracy -0.58847793  0.7029752
HS Grad     0.58221620 -0.4879710
```



