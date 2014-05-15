REPRODUCIBLE RESEARCH PEER ASSESSMENT ASSIGNMENT
========================================================

This is an R Markdown document showing answers to the assignment for Reproducble Research course as part of the Data Science specialization. The questionas are answered in a sequential manner.

To load data into R Studio


```r
activity <- read.csv("C:/Users/Zilon/Desktop/activity.csv", dec = ",")
```


To make an Histogram of the total number of steps taken each day

```r
hist(activity$steps)
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 


To calculate the median and mean of the total steps taken each day

```r
summary(activity$steps)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
##     0.0     0.0     0.0    37.4    12.0   806.0    2304
```


To draw a time series plot of the 5 minutes interval on the x-axis and the average number of steps taken, veraged across all days on the y-axis.

```r
plot(activity$interval, activity$steps, type = "l")
```

![plot of chunk time series plot](figure/time_series_plot.png) 



Inputing Missing values
========================================================
To count and report the number of missing values in the whole dataset

```r
sum(!complete.cases(activity))
```

```
## [1] 2304
```


To fill in the misssing values

```r
activity$steps[is.na(activity$steps)] <- mean(activity$steps, na.rm = TRUE)
```

To view changes (mean and median) to the new dataset after filling missing values 

```r
summary(activity$steps)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     0.0     0.0     0.0    37.4    37.4   806.0
```


To draw the histogram of the new dataset of the steps taken each day

```r
hist(activity$steps)
```

![plot of chunk Histogram of steps taken each day after removing missing values](figure/Histogram_of_steps_taken_each_day_after_removing_missing_values.png) 

There seems to be no difference in the dataset when after missing values were removed. The major impact was mainly in increasing the average total steps taken per day. Also, the 3rd Quartile increased from 16 to 37.4.
