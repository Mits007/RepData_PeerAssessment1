# Reproducible Research: Peer Assessment 1
==========================================



## Loading and preprocessing the data

```r
data_file = read.csv("./activity.csv", stringsAsFactors = FALSE, header = TRUE, 
    na.string = "NA")
data_file$date = as.Date(data_file$date)
```


## What is mean total number of steps taken per day?

```r
library(reshape)
datamelt = melt(data_file, id = c("date"), measure.vars = c("steps"))
steps_count = cast(datamelt, date ~ variable, sum)
```


- Plot the Histogram

```r
plot(steps_count, type = "h", lwd = 20)
```

![plot of chunk plothistogram](figure/plothistogram.png) 


- Calculate and report the mean steps taken every day

```r
meansteps = cast(datamelt, date ~ variable, mean, na.rm = TRUE)
names(meansteps) = c("date", "mean_steps")
print(meansteps)
```

```
##          date mean_steps
## 1  2012-10-01        NaN
## 2  2012-10-02     0.4375
## 3  2012-10-03    39.4167
## 4  2012-10-04    42.0694
## 5  2012-10-05    46.1597
## 6  2012-10-06    53.5417
## 7  2012-10-07    38.2465
## 8  2012-10-08        NaN
## 9  2012-10-09    44.4826
## 10 2012-10-10    34.3750
## 11 2012-10-11    35.7778
## 12 2012-10-12    60.3542
## 13 2012-10-13    43.1458
## 14 2012-10-14    52.4236
## 15 2012-10-15    35.2049
## 16 2012-10-16    52.3750
## 17 2012-10-17    46.7083
## 18 2012-10-18    34.9167
## 19 2012-10-19    41.0729
## 20 2012-10-20    36.0938
## 21 2012-10-21    30.6285
## 22 2012-10-22    46.7361
## 23 2012-10-23    30.9653
## 24 2012-10-24    29.0104
## 25 2012-10-25     8.6528
## 26 2012-10-26    23.5347
## 27 2012-10-27    35.1354
## 28 2012-10-28    39.7847
## 29 2012-10-29    17.4236
## 30 2012-10-30    34.0938
## 31 2012-10-31    53.5208
## 32 2012-11-01        NaN
## 33 2012-11-02    36.8056
## 34 2012-11-03    36.7049
## 35 2012-11-04        NaN
## 36 2012-11-05    36.2465
## 37 2012-11-06    28.9375
## 38 2012-11-07    44.7326
## 39 2012-11-08    11.1771
## 40 2012-11-09        NaN
## 41 2012-11-10        NaN
## 42 2012-11-11    43.7778
## 43 2012-11-12    37.3785
## 44 2012-11-13    25.4722
## 45 2012-11-14        NaN
## 46 2012-11-15     0.1424
## 47 2012-11-16    18.8924
## 48 2012-11-17    49.7882
## 49 2012-11-18    52.4653
## 50 2012-11-19    30.6979
## 51 2012-11-20    15.5278
## 52 2012-11-21    44.3993
## 53 2012-11-22    70.9271
## 54 2012-11-23    73.5903
## 55 2012-11-24    50.2708
## 56 2012-11-25    41.0903
## 57 2012-11-26    38.7569
## 58 2012-11-27    47.3819
## 59 2012-11-28    35.3576
## 60 2012-11-29    24.4688
## 61 2012-11-30        NaN
```


- Calculate and report the median steps taken every day

```r
mediansteps = cast(datamelt, date ~ variable, median, na.rm = TRUE)
names(mediansteps) = c("date", "median_steps")
print(mediansteps)
```

```
##          date median_steps
## 1  2012-10-01           NA
## 2  2012-10-02            0
## 3  2012-10-03            0
## 4  2012-10-04            0
## 5  2012-10-05            0
## 6  2012-10-06            0
## 7  2012-10-07            0
## 8  2012-10-08           NA
## 9  2012-10-09            0
## 10 2012-10-10            0
## 11 2012-10-11            0
## 12 2012-10-12            0
## 13 2012-10-13            0
## 14 2012-10-14            0
## 15 2012-10-15            0
## 16 2012-10-16            0
## 17 2012-10-17            0
## 18 2012-10-18            0
## 19 2012-10-19            0
## 20 2012-10-20            0
## 21 2012-10-21            0
## 22 2012-10-22            0
## 23 2012-10-23            0
## 24 2012-10-24            0
## 25 2012-10-25            0
## 26 2012-10-26            0
## 27 2012-10-27            0
## 28 2012-10-28            0
## 29 2012-10-29            0
## 30 2012-10-30            0
## 31 2012-10-31            0
## 32 2012-11-01           NA
## 33 2012-11-02            0
## 34 2012-11-03            0
## 35 2012-11-04           NA
## 36 2012-11-05            0
## 37 2012-11-06            0
## 38 2012-11-07            0
## 39 2012-11-08            0
## 40 2012-11-09           NA
## 41 2012-11-10           NA
## 42 2012-11-11            0
## 43 2012-11-12            0
## 44 2012-11-13            0
## 45 2012-11-14           NA
## 46 2012-11-15            0
## 47 2012-11-16            0
## 48 2012-11-17            0
## 49 2012-11-18            0
## 50 2012-11-19            0
## 51 2012-11-20            0
## 52 2012-11-21            0
## 53 2012-11-22            0
## 54 2012-11-23            0
## 55 2012-11-24            0
## 56 2012-11-25            0
## 57 2012-11-26            0
## 58 2012-11-27            0
## 59 2012-11-28            0
## 60 2012-11-29            0
## 61 2012-11-30           NA
```


## What is the average daily activity pattern?

```r
datamelt2 = melt(data_file, id = c("interval"), measure.vars = c("steps"))
average_steps = cast(datamelt2, interval ~ variable, mean, na.rm = TRUE)
names(average_steps) = c("interval", "avsteps")
```


- Plot the timeseries

```r
plot(average_steps, type = "l")
```

![plot of chunk plottimeseries](figure/plottimeseries.png) 


- Calculate max # of steps for an interval across all days 

```r
max_value = max(average_steps$avsteps)
interval_number = average_steps[average_steps$avsteps == max_value, "interval"]
cat("The interval with max number of steps averaged across all days is = ", 
    interval_number)
```

```
## The interval with max number of steps averaged across all days is =  835
```

## Imputing missing values

-Missing Values

```r
num_complete_cases = sum(!complete.cases(data_file))
cat("No. of missing values is=", num_complete_cases)
```

```
## No. of missing values is= 2304
```

- Create new dataset with missing values filled in: The strategy is to fill up the missing values with the mean for that 5-minute interval. The code iterates over the entire dataset. Wherever the # of steps is NA, it fills it up with the mean value of the steps taken in that 5-minute interval

```r
new_data_file = data_file
for (i in 1:nrow(data_file)) {
    if (is.na(data_file[i, "steps"])) {
        key_interval = data_file[i, "interval"]
        new_data_file[i, "steps"] = average_steps[average_steps$interval == 
            key_interval, "avsteps"]
    }
}
```


- Histogram of NEW total # of steps taken each day

```r
new_datamelt = melt(new_data_file, id = c("date"), measure.vars = c("steps"))
steps_count = cast(new_datamelt, date ~ variable, sum)
plot(steps_count, type = "h", lwd = 20)
```

![plot of chunk newtotalsteps](figure/newtotalsteps.png) 


- Calculate the new mean steps taken per day

```r
new_meansteps = cast(new_datamelt, date ~ variable, mean, na.rm = TRUE)
names(new_meansteps) = c("date", "mean_steps")
print(new_meansteps)
```

```
##          date mean_steps
## 1  2012-10-01    37.3826
## 2  2012-10-02     0.4375
## 3  2012-10-03    39.4167
## 4  2012-10-04    42.0694
## 5  2012-10-05    46.1597
## 6  2012-10-06    53.5417
## 7  2012-10-07    38.2465
## 8  2012-10-08    37.3826
## 9  2012-10-09    44.4826
## 10 2012-10-10    34.3750
## 11 2012-10-11    35.7778
## 12 2012-10-12    60.3542
## 13 2012-10-13    43.1458
## 14 2012-10-14    52.4236
## 15 2012-10-15    35.2049
## 16 2012-10-16    52.3750
## 17 2012-10-17    46.7083
## 18 2012-10-18    34.9167
## 19 2012-10-19    41.0729
## 20 2012-10-20    36.0938
## 21 2012-10-21    30.6285
## 22 2012-10-22    46.7361
## 23 2012-10-23    30.9653
## 24 2012-10-24    29.0104
## 25 2012-10-25     8.6528
## 26 2012-10-26    23.5347
## 27 2012-10-27    35.1354
## 28 2012-10-28    39.7847
## 29 2012-10-29    17.4236
## 30 2012-10-30    34.0938
## 31 2012-10-31    53.5208
## 32 2012-11-01    37.3826
## 33 2012-11-02    36.8056
## 34 2012-11-03    36.7049
## 35 2012-11-04    37.3826
## 36 2012-11-05    36.2465
## 37 2012-11-06    28.9375
## 38 2012-11-07    44.7326
## 39 2012-11-08    11.1771
## 40 2012-11-09    37.3826
## 41 2012-11-10    37.3826
## 42 2012-11-11    43.7778
## 43 2012-11-12    37.3785
## 44 2012-11-13    25.4722
## 45 2012-11-14    37.3826
## 46 2012-11-15     0.1424
## 47 2012-11-16    18.8924
## 48 2012-11-17    49.7882
## 49 2012-11-18    52.4653
## 50 2012-11-19    30.6979
## 51 2012-11-20    15.5278
## 52 2012-11-21    44.3993
## 53 2012-11-22    70.9271
## 54 2012-11-23    73.5903
## 55 2012-11-24    50.2708
## 56 2012-11-25    41.0903
## 57 2012-11-26    38.7569
## 58 2012-11-27    47.3819
## 59 2012-11-28    35.3576
## 60 2012-11-29    24.4688
## 61 2012-11-30    37.3826
```


- Calculate the new median steps taken per day

```r
new_mediansteps = cast(new_datamelt, date ~ variable, median, na.rm = TRUE)
names(new_mediansteps) = c("date", "median_steps")
print(new_mediansteps)
```

```
##          date median_steps
## 1  2012-10-01        34.11
## 2  2012-10-02         0.00
## 3  2012-10-03         0.00
## 4  2012-10-04         0.00
## 5  2012-10-05         0.00
## 6  2012-10-06         0.00
## 7  2012-10-07         0.00
## 8  2012-10-08        34.11
## 9  2012-10-09         0.00
## 10 2012-10-10         0.00
## 11 2012-10-11         0.00
## 12 2012-10-12         0.00
## 13 2012-10-13         0.00
## 14 2012-10-14         0.00
## 15 2012-10-15         0.00
## 16 2012-10-16         0.00
## 17 2012-10-17         0.00
## 18 2012-10-18         0.00
## 19 2012-10-19         0.00
## 20 2012-10-20         0.00
## 21 2012-10-21         0.00
## 22 2012-10-22         0.00
## 23 2012-10-23         0.00
## 24 2012-10-24         0.00
## 25 2012-10-25         0.00
## 26 2012-10-26         0.00
## 27 2012-10-27         0.00
## 28 2012-10-28         0.00
## 29 2012-10-29         0.00
## 30 2012-10-30         0.00
## 31 2012-10-31         0.00
## 32 2012-11-01        34.11
## 33 2012-11-02         0.00
## 34 2012-11-03         0.00
## 35 2012-11-04        34.11
## 36 2012-11-05         0.00
## 37 2012-11-06         0.00
## 38 2012-11-07         0.00
## 39 2012-11-08         0.00
## 40 2012-11-09        34.11
## 41 2012-11-10        34.11
## 42 2012-11-11         0.00
## 43 2012-11-12         0.00
## 44 2012-11-13         0.00
## 45 2012-11-14        34.11
## 46 2012-11-15         0.00
## 47 2012-11-16         0.00
## 48 2012-11-17         0.00
## 49 2012-11-18         0.00
## 50 2012-11-19         0.00
## 51 2012-11-20         0.00
## 52 2012-11-21         0.00
## 53 2012-11-22         0.00
## 54 2012-11-23         0.00
## 55 2012-11-24         0.00
## 56 2012-11-25         0.00
## 57 2012-11-26         0.00
## 58 2012-11-27         0.00
## 59 2012-11-28         0.00
## 60 2012-11-29         0.00
## 61 2012-11-30        34.11
```


## Are there differences in activity patterns between weekdays and weekends?
- Create a new factor variable in the dataset with levels - weekday and weekend

```r
new_data_file$weekdays = ifelse(weekdays(new_data_file$date) %in% c("Saturday", 
    "Sunday"), "weekend", "weekday")
```

- Calculate the mean # of steps over weekday and weekend

```r
datamelt3 = melt(new_data_file, id = c("interval", "weekdays"), measure.vars = c("steps"))
avg_steps = cast(datamelt3, interval + weekdays ~ variable, mean)
```

- Plot the mean steps for weekend and weekday

```r
library(lattice)
xyplot(avg_steps$steps ~ avg_steps$interval | avg_steps$weekdays, data = avg_steps, 
    layout = c(1, 2), type = "l", xlab = "Interval", ylab = "Number of Steps")
```

![plot of chunk plotweekdaysmean](figure/plotweekdaysmean.png) 

