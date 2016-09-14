# Missing Values
* Instead of removing rows, specific columns can be set as missing values to tell R to avoid those columns
* NA represents missing information
* NA + 3, NA == 3 etc always returns NA
* summary(diamonds$x) returns a summary of entire dataset wrt column "x"
* diamonds$x[diamonds$x == 0] returns "x" values of all rows where x == 0
* diamonds$x[diamonds$x == 0] <- NA, value of "x" to NA in all rows where x == 0