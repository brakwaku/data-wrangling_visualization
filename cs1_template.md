---
title: "Up and Running with R"
author: "Kwaku Appau-Nkansah"
date: "April 23, 2021"
output:
  html_document:
    theme: cerulean  
    keep_md: true
    code_folding: hide
    toc: true
    toc_float: true
    fig_height: 6
    fig_width: 12
    fig_align: 'center'
---



## Reading Notes

One key thing I learned was that in R, variables are stored
as objects. This is different from a lot of programming
languages I am familiar with except python.

I also learned that object names must start with a **letter**, and can only contain:

- *letters*
- *numbers*
- *_*
- *.*

If you type an object's name, you can inspect that object.

R sreports errors, warnings, and messages in red font but
seeing a red text is not always bad.


## R Practice

### Question 1

Create an object named `object1` and assign it the value of `10`. Create another object named `object2` and assign it the value of `"BYU-Idaho"`. Then try to add the two values together.


**What error message do you get?** Error in object1 + object2 : non-numeric argument
to binary operator

**What is this error message trying to tell you?** It is telling  me that I am trying to add something that is not a binary operand.


```r
object1 <- 10
object2 <- "BYU-Idaho"
(object1 + object2)
```

```
## Error in object1 + object2: non-numeric argument to binary operator
```
### Question 2

Write a function that takes two numbers as input and returns their mean. (Do not use the built in `mean()` function.) Use your function to assign the mean of 28 and 14 to an object called `result`. Display `result`.


```r
result <- function(int1, int2) {
  (int1 + int2) / 2
}

result(14, 28)
```

```
## [1] 21
```

### Question 3

Create a vector that contains the temperatures 85, 83, 83, 89, 92, 87, and 84. Then calculate:

- The mean of the temperatures
- The standard deviation of the temperatures
- The deviation of each temperature from the mean temperature 


```r
df <- c(85, 83, 83, 89, 92, 87,84)
round(mean(df), digits = 3)
```

```
## [1] 86.143
```

```r
sd(df)
```

```
## [1] 3.387653
```

```r
the_deviation <- df - mean(df)
the_deviation
```

```
## [1] -1.1428571 -3.1428571 -3.1428571  2.8571429  5.8571429  0.8571429 -2.1428571
```

### Question 4

Create a vector `v` with all integers 0-30, and a vector `w` with every third integer in the same range. (The documentation for `?seq` might be helpful.)

Calculate the difference in lengths of the vectors `v` and `w`. 


```r
v <- seq(0, 30)
w <- seq(0, 30, by=3)

v_len <- length(v)
w_len <- length(w)

difference <- v_len - w_len
difference
```

```
## [1] 20
```

### Question 5

Create a new vector `v_square` with the square of elements at indices 3, 6, 7, 10, 15, 22, 23, 24, and 30 from the variable `v`. Display `v_square`.


```r
v_square <- (v[c(3, 6, 7, 10, 15, 22, 23, 24, 30)])^2
v_square
```

```
## [1]   4  25  36  81 196 441 484 529 841
```

### Question 6

Create a boolean vector `v_bool` indicating which vector `v` elements are bigger than 20. Display `v_bool`. Then calculate how many values are over 20. (Hint: In R, TRUE = 1, and FALSE = 0, so you can use simple arithmetic to find this out.)


```r
v_bool <- v > 20
v_bool
```

```
##  [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
## [13] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE
## [25]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
```

```r
sum(v_bool)
```

```
## [1] 10
```

### Question 7

Display the output of `v[TRUE]`. 

**Explain why you think R outputs this.** Type your answer here.


```r
v[TRUE]
```

```
##  [1]  0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
## [26] 25 26 27 28 29 30
```

### Question 8

Use the variable `v_bool` as an index to extract the elements from `v` that are bigger than 20. Calculate the min and max values of this new vector.


```r
new_v <- v[v_bool]
min(new_v)
```

```
## [1] 21
```

```r
max(new_v)
```

```
## [1] 30
```

### Question 9

What are the column names of the built-in dataframe `beaver1`? How many observations (rows) and variables (columns) are there?


```r
colnames(beaver1)
```

```
## [1] "day"   "time"  "temp"  "activ"
```

```r
ncol(beaver1)
```

```
## [1] 4
```

### Question 10

Use square bracket notation to index the `beaver1` data set. Display the values in rows 21-23, columns 3-4.


```r
beaver1[21:23, 3:4]
```

```
##     temp activ
## 21 36.78     0
## 22 36.82     0
## 23 36.89     0
```

### Question 11

What is the min, mean, and max body temperature in the `beaver1` data set?


```r
min(beaver1$temp)
```

```
## [1] 36.33
```

```r
mean(beaver1$temp)
```

```
## [1] 36.86219
```

```r
max(beaver1$temp)
```

```
## [1] 37.53
```

### Question 12

In the `beaver1` data set the variable `temp` is recorded in degrees Celsius. Run the code below, which is trying to convert `temp` to Fahrenheit.

**What error message do you get?** Error in c_to_f(beaverl$temp) : object 'beaverl' not found

**What is this error message trying to tell you?** The object we are trying to work on cannot be found. This is because their spellings are not the same.


```r
# function to convert Celsius to Fahrenheit
c_to_f <- function(c){
  f = (c * 9/5) + 32
  return(f)
}

# make a new vector of Fahrenheit temperatures!
temp_in_f <- c_to_f(beaverl$temp)
```

```
## Error in c_to_f(beaverl$temp): object 'beaverl' not found
```
