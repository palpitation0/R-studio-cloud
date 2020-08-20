R cloud - github
================

``` r
library(MASS)
head(Cars93)
```

    ##   Manufacturer   Model    Type Min.Price Price Max.Price MPG.city MPG.highway
    ## 1        Acura Integra   Small      12.9  15.9      18.8       25          31
    ## 2        Acura  Legend Midsize      29.2  33.9      38.7       18          25
    ## 3         Audi      90 Compact      25.9  29.1      32.3       20          26
    ## 4         Audi     100 Midsize      30.8  37.7      44.6       19          26
    ## 5          BMW    535i Midsize      23.7  30.0      36.2       22          30
    ## 6        Buick Century Midsize      14.2  15.7      17.3       22          31
    ##              AirBags DriveTrain Cylinders EngineSize Horsepower  RPM
    ## 1               None      Front         4        1.8        140 6300
    ## 2 Driver & Passenger      Front         6        3.2        200 5500
    ## 3        Driver only      Front         6        2.8        172 5500
    ## 4 Driver & Passenger      Front         6        2.8        172 5500
    ## 5        Driver only       Rear         4        3.5        208 5700
    ## 6        Driver only      Front         4        2.2        110 5200
    ##   Rev.per.mile Man.trans.avail Fuel.tank.capacity Passengers Length Wheelbase
    ## 1         2890             Yes               13.2          5    177       102
    ## 2         2335             Yes               18.0          5    195       115
    ## 3         2280             Yes               16.9          5    180       102
    ## 4         2535             Yes               21.1          6    193       106
    ## 5         2545             Yes               21.1          4    186       109
    ## 6         2565              No               16.4          6    189       105
    ##   Width Turn.circle Rear.seat.room Luggage.room Weight  Origin          Make
    ## 1    68          37           26.5           11   2705 non-USA Acura Integra
    ## 2    71          38           30.0           15   3560 non-USA  Acura Legend
    ## 3    67          37           28.0           14   3375 non-USA       Audi 90
    ## 4    70          37           31.0           17   3405 non-USA      Audi 100
    ## 5    69          39           27.0           13   3640 non-USA      BMW 535i
    ## 6    69          41           28.0           16   2880     USA Buick Century

``` r
str(Cars93)
```

    ## 'data.frame':    93 obs. of  27 variables:
    ##  $ Manufacturer      : Factor w/ 32 levels "Acura","Audi",..: 1 1 2 2 3 4 4 4 4 5 ...
    ##  $ Model             : Factor w/ 93 levels "100","190E","240",..: 49 56 9 1 6 24 54 74 73 35 ...
    ##  $ Type              : Factor w/ 6 levels "Compact","Large",..: 4 3 1 3 3 3 2 2 3 2 ...
    ##  $ Min.Price         : num  12.9 29.2 25.9 30.8 23.7 14.2 19.9 22.6 26.3 33 ...
    ##  $ Price             : num  15.9 33.9 29.1 37.7 30 15.7 20.8 23.7 26.3 34.7 ...
    ##  $ Max.Price         : num  18.8 38.7 32.3 44.6 36.2 17.3 21.7 24.9 26.3 36.3 ...
    ##  $ MPG.city          : int  25 18 20 19 22 22 19 16 19 16 ...
    ##  $ MPG.highway       : int  31 25 26 26 30 31 28 25 27 25 ...
    ##  $ AirBags           : Factor w/ 3 levels "Driver & Passenger",..: 3 1 2 1 2 2 2 2 2 2 ...
    ##  $ DriveTrain        : Factor w/ 3 levels "4WD","Front",..: 2 2 2 2 3 2 2 3 2 2 ...
    ##  $ Cylinders         : Factor w/ 6 levels "3","4","5","6",..: 2 4 4 4 2 2 4 4 4 5 ...
    ##  $ EngineSize        : num  1.8 3.2 2.8 2.8 3.5 2.2 3.8 5.7 3.8 4.9 ...
    ##  $ Horsepower        : int  140 200 172 172 208 110 170 180 170 200 ...
    ##  $ RPM               : int  6300 5500 5500 5500 5700 5200 4800 4000 4800 4100 ...
    ##  $ Rev.per.mile      : int  2890 2335 2280 2535 2545 2565 1570 1320 1690 1510 ...
    ##  $ Man.trans.avail   : Factor w/ 2 levels "No","Yes": 2 2 2 2 2 1 1 1 1 1 ...
    ##  $ Fuel.tank.capacity: num  13.2 18 16.9 21.1 21.1 16.4 18 23 18.8 18 ...
    ##  $ Passengers        : int  5 5 5 6 4 6 6 6 5 6 ...
    ##  $ Length            : int  177 195 180 193 186 189 200 216 198 206 ...
    ##  $ Wheelbase         : int  102 115 102 106 109 105 111 116 108 114 ...
    ##  $ Width             : int  68 71 67 70 69 69 74 78 73 73 ...
    ##  $ Turn.circle       : int  37 38 37 37 39 41 42 45 41 43 ...
    ##  $ Rear.seat.room    : num  26.5 30 28 31 27 28 30.5 30.5 26.5 35 ...
    ##  $ Luggage.room      : int  11 15 14 17 13 16 17 21 14 18 ...
    ##  $ Weight            : int  2705 3560 3375 3405 3640 2880 3470 4105 3495 3620 ...
    ##  $ Origin            : Factor w/ 2 levels "USA","non-USA": 2 2 2 2 2 1 1 1 1 1 ...
    ##  $ Make              : Factor w/ 93 levels "Acura Integra",..: 1 2 4 3 5 6 7 9 8 10 ...

``` r
Cars93$Type
```

    ##  [1] Small   Midsize Compact Midsize Midsize Midsize Large   Large   Midsize
    ## [10] Large   Midsize Compact Compact Sporty  Midsize Van     Van     Large  
    ## [19] Sporty  Large   Compact Large   Small   Small   Compact Van     Midsize
    ## [28] Sporty  Small   Large   Small   Small   Compact Sporty  Sporty  Van    
    ## [37] Midsize Large   Small   Sporty  Sporty  Small   Compact Small   Small  
    ## [46] Sporty  Midsize Midsize Midsize Midsize Midsize Large   Small   Small  
    ## [55] Compact Van     Sporty  Compact Midsize Sporty  Midsize Small   Midsize
    ## [64] Small   Compact Van     Midsize Compact Midsize Van     Large   Sporty 
    ## [73] Small   Compact Sporty  Midsize Large   Compact Small   Small   Small  
    ## [82] Compact Small   Small   Sporty  Midsize Van     Small   Van     Compact
    ## [91] Sporty  Compact Midsize
    ## Levels: Compact Large Midsize Small Sporty Van

``` r
table(Cars93$Type)
```

    ## 
    ## Compact   Large Midsize   Small  Sporty     Van 
    ##      16      11      22      21      14       9

``` r
prop.table(table(Cars93$Type))
```

    ## 
    ##    Compact      Large    Midsize      Small     Sporty        Van 
    ## 0.17204301 0.11827957 0.23655914 0.22580645 0.15053763 0.09677419

``` r
table(Cars93$Origin)
```

    ## 
    ##     USA non-USA 
    ##      48      45

``` r
prop.table(table(Cars93$Origin))
```

    ## 
    ##      USA  non-USA 
    ## 0.516129 0.483871

``` r
table(Cars93$Type, Cars93$Origin)
```

    ##          
    ##           USA non-USA
    ##   Compact   7       9
    ##   Large    11       0
    ##   Midsize  10      12
    ##   Small     7      14
    ##   Sporty    8       6
    ##   Van       5       4

``` r
tab1 <- table(Cars93$Type, Cars93$Origin)
rowSums(tab1)
```

    ## Compact   Large Midsize   Small  Sporty     Van 
    ##      16      11      22      21      14       9

``` r
colSums(tab1)
```

    ##     USA non-USA 
    ##      48      45

``` r
prop.table(tab1)
```

    ##          
    ##                  USA    non-USA
    ##   Compact 0.07526882 0.09677419
    ##   Large   0.11827957 0.00000000
    ##   Midsize 0.10752688 0.12903226
    ##   Small   0.07526882 0.15053763
    ##   Sporty  0.08602151 0.06451613
    ##   Van     0.05376344 0.04301075

``` r
prop.table(tab1)*100
```

    ##          
    ##                 USA   non-USA
    ##   Compact  7.526882  9.677419
    ##   Large   11.827957  0.000000
    ##   Midsize 10.752688 12.903226
    ##   Small    7.526882 15.053763
    ##   Sporty   8.602151  6.451613
    ##   Van      5.376344  4.301075

``` r
chisq.test(Cars93$Type, Cars93$Origin)
```

    ## Warning in chisq.test(Cars93$Type, Cars93$Origin): Chi-squared approximation may
    ## be incorrect

    ## 
    ##  Pearson's Chi-squared test
    ## 
    ## data:  Cars93$Type and Cars93$Origin
    ## X-squared = 14.08, df = 5, p-value = 0.01511

``` r
fisher.test(Cars93$Type, Cars93$Origin)
```

    ## 
    ##  Fisher's Exact Test for Count Data
    ## 
    ## data:  Cars93$Type and Cars93$Origin
    ## p-value = 0.007248
    ## alternative hypothesis: two.sided

``` r
install.packages("DescTools")
```

    ## Installing package into '/home/rstudio-user/R/x86_64-pc-linux-gnu-library/4.0'
    ## (as 'lib' is unspecified)

``` r
library(DescTools)
GTest(Cars93$Type, Cars93$Origin)
```

    ## 
    ##  Log likelihood ratio (G-test) test of independence without correction
    ## 
    ## data:  Cars93$Type and Cars93$Origin
    ## G = 18.362, X-squared df = 5, p-value = 0.002526

``` r
tab3 <- table(Cars93$Man.trans.avail, Cars93$Origin)
tab3
```

    ##      
    ##       USA non-USA
    ##   No   26       6
    ##   Yes  22      39

``` r
chisq.test(tab3)
```

    ## 
    ##  Pearson's Chi-squared test with Yates' continuity correction
    ## 
    ## data:  tab3
    ## X-squared = 15.397, df = 1, p-value = 8.712e-05

``` r
 # Yate's correction ; subtracts 0.5 from each cell
```

``` r
table(Cars93$Man.trans.avail, Cars93$Origin, Cars93$Type)
```

    ## , ,  = Compact
    ## 
    ##      
    ##       USA non-USA
    ##   No    2       0
    ##   Yes   5       9
    ## 
    ## , ,  = Large
    ## 
    ##      
    ##       USA non-USA
    ##   No   11       0
    ##   Yes   0       0
    ## 
    ## , ,  = Midsize
    ## 
    ##      
    ##       USA non-USA
    ##   No    9       4
    ##   Yes   1       8
    ## 
    ## , ,  = Small
    ## 
    ##      
    ##       USA non-USA
    ##   No    0       0
    ##   Yes   7      14
    ## 
    ## , ,  = Sporty
    ## 
    ##      
    ##       USA non-USA
    ##   No    0       0
    ##   Yes   8       6
    ## 
    ## , ,  = Van
    ## 
    ##      
    ##       USA non-USA
    ##   No    4       2
    ##   Yes   1       2

``` r
ftable(Cars93$Man.trans.avail, Cars93$Origin, Cars93$Type)
```

    ##              Compact Large Midsize Small Sporty Van
    ##                                                    
    ## No  USA            2    11       9     0      0   4
    ##     non-USA        0     0       4     0      0   2
    ## Yes USA            5     0       1     7      8   1
    ##     non-USA        9     0       8    14      6   2

``` r
mantelhaen.test(Cars93$Man.trans.avail, Cars93$Origin, Cars93$Type)
```

    ## 
    ##  Mantel-Haenszel chi-squared test with continuity correction
    ## 
    ## data:  Cars93$Man.trans.avail and Cars93$Origin and Cars93$Type
    ## Mantel-Haenszel X-squared = 8.0153, df = 1, p-value = 0.004638
    ## alternative hypothesis: true common odds ratio is not equal to 1
    ## 95 percent confidence interval:
    ##   2.226531 76.891307
    ## sample estimates:
    ## common odds ratio 
    ##          13.08438

``` r
CramerV(Cars93$Type, Cars93$Origin)
```

    ## [1] 0.3890967

``` r
# 0 =< V =< 1
# The larger V is, the stronger the relationship
# V=0 can be interpreted as independence
# No reference for weak/moderate/strong association
```
