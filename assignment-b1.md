Assignment B-1: Making a Function
================
Dana Halay
2023-11-03

### Exercise 1: Make a Function / Exercise 2: Document Your Function

Here I will make a function that when given a number of minutes, will
convert it to the number of hours. Then, I will document the function
using roxygen2 tags.

``` r
mins_to_hours <- function(mins) { 
  if(!is.numeric(mins)) {
    stop('I am so sorry, but this function only works for numeric input!\n',
         'You have provided an object of class: ', class(mins)[1]) #this is creating a function, and stating the input must be numeric, and gives an error message for when it is not numeric 
  }
  ((mins) / 60) #this specifies the function 
}

#' @title mins_to_hours
#' @description mins_to_hours returns the numeric value converted from a measurement in minutes to a measurement in hours 
#' @param mins is a numeric, atomic, or vector. I named it "mins" because it should be an input of a number of minutes which will be converted to a number of hours. 
#' @return a numeric of the value divided by 60 
#' @examples
#' mins_to_hours(60)
#' mins_to_hours(1:5)
```

### Exercise 3: Include Examples

Here I will show examples of ways that the *mins_to_hours* function can
be used with numeric inputs. I will also show an example of a way that
the function cannot be used when using a non-numeric input.

``` r
#Example 1: Correct way to use the function 
mins_to_hours(90)
```

    ## [1] 1.5

``` r
#Example 2: Correct way to use the function
mins_to_hours(1:5)
```

    ## [1] 0.01666667 0.03333333 0.05000000 0.06666667 0.08333333

``` r
#Example 3: Incorrect way to use the function 
mins_to_hours(banana)
```

    ## Error in mins_to_hours(banana): object 'banana' not found

### Exercise 4: Test the Function

Here I will write formal tests for my function using the *testthat*
package and the *expects_equal()* function.

``` r
library(testthat) #this is loading the library for the testthat package 
```

    ## Warning: package 'testthat' was built under R version 4.2.3

``` r
test_that("Basic functionalities",{
  expect_equal(mins_to_hours(60), 1) 
  expect_equal(mins_to_hours(10:12), c(0.1666667, 0.1833333, 0.2000000), tolerance=1e-6)
  expect_equal(mins_to_hours(0), 0) 
}) #this is testing 3 different inputs: a regular numeric value, a series of numeric values, and vector of length zero. The series of numeric values has tolerance specified because the numbers are rounded. 
```

    ## Test passed 🥳
