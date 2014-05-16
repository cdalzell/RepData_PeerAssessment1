# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
unzip("activity.zip")

activityDF <- read.csv("activity.csv")
```


## What is mean total number of steps taken per day?

Make a histogram of the total number of steps taken each day

```r
stepsPerDay <- aggregate(steps ~ date, data = activityDF, FUN = sum)

hist(stepsPerDay$steps, breaks = nrow(stepsPerDay), main = "", xlab = "Steps Per Day", 
    ylab = "Frequency", col = "lightblue")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 


Calculate and report the mean and median total number of steps taken per day

```r
meanStepsPerDay <- mean(stepsPerDay$steps)
medianStepsPerDay <- median(stepsPerDay$steps)
```


Mean number of steps taken per day: 10766

Median number of steps taken per day: 10765

## What is the average daily activity pattern?

Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)

```r
avg5Min <- aggregate(steps ~ interval, data = activityDF, FUN = mean)

plot(avg5Min, type = "l", xlab = "Intervals", ylab = "Steps")
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 


Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?

```r
maxInterval <- avg5Min[which.max(avg5Min$steps), "interval"]
```


Interval with the maximum number of steps: 835

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
