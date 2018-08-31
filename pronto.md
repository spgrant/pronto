---
title: "Pronto bikeshare trips"
author: "Shannon Grant"
date: "2018-08-31"
output:
  html_document:
    keep_md: yes
---




```r
# Pronto trip data downloaded 8/31/18 
#    https://data.seattle.gov/Community/Pronto-Cycle-Share-Trip-Data/tw7j-dfaw
 
trips <- read_csv("Pronto_Cycle_Share_Trip_Data.csv")
```

```
## Parsed with column specification:
## cols(
##   trip_id = col_integer(),
##   starttime = col_character(),
##   stoptime = col_character(),
##   bikeid = col_character(),
##   tripduration = col_double(),
##   from_station_name = col_character(),
##   to_station_name = col_character(),
##   from_station_id = col_character(),
##   to_station_id = col_character(),
##   usertype = col_character(),
##   gender = col_character(),
##   birthyear = col_integer()
## )
```

```r
length(rownames(trips))
```

```
## [1] 275091
```

```r
# want a few variables to plot, for better GitHub and Rprog practice
head(trips)
```

```
## # A tibble: 6 x 12
##   trip_id starttime stoptime bikeid tripduration from_station_na~
##     <int> <chr>     <chr>    <chr>         <dbl> <chr>           
## 1     431 10/13/20~ 10/13/2~ SEA00~         986. 2nd Ave & Sprin~
## 2     432 10/13/20~ 10/13/2~ SEA00~         926. 2nd Ave & Sprin~
## 3     433 10/13/20~ 10/13/2~ SEA00~         884. 2nd Ave & Sprin~
## 4     434 10/13/20~ 10/13/2~ SEA00~         866. 2nd Ave & Sprin~
## 5     435 10/13/20~ 10/13/2~ SEA00~         924. 2nd Ave & Sprin~
## 6     436 10/13/20~ 10/13/2~ SEA00~         809. 2nd Ave & Sprin~
## # ... with 6 more variables: to_station_name <chr>, from_station_id <chr>,
## #   to_station_id <chr>, usertype <chr>, gender <chr>, birthyear <int>
```

```r
trips$tripyear <- str_sub(trips$starttime, 7,10)

# check for missingness
summary(trips$birthyear)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
##    1931    1974    1983    1980    1987    1999  101280
```

```r
table(trips$gender)
```

```
## 
## Female   Male  Other 
##  34997 135171   3647
```

```r
table(trips$tripyear)
```

```
## 
##   2014   2015   2016   2017 
##  20239 140291 102606  11955
```


## Trips by gender and year

The dataset does not include a rider ID.

![](pronto_files/figure-html/trip_gender_year-1.png)<!-- -->

