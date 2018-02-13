#### Data Transformation
- usually need to transform data before you can use it since it's not given to you in the perfect format
- use `dplyr` package, which is part of `tidyverse`
- some functions, such as filter(), come with base R but are overwritten by dplyr
  - to use the correct one, `stats::filter()` or `dplyr::filter()`

- tibbles are data frames but slightly modified to be more efficient in tidyverse

- type of each variable is displayed under each column:
  - `int` stands for integers
  - `dbl` stands for doubles or real numbers
  - `chr` stands for character vectors or strings
  - `dttm` stands for date-times (a date + a time)
  - `lgl` stands for logical, vectors that only contain `TRUE` or `FALSE`
  - fctr stands for factors, which R uses to represent categorical variables with fixed possible values
  - `date` stands for dates
  
###### Dplyr Basics
- 5 main functions that allow me to solve vast majority of data manipulation challenges:
  - `filter()` to pick observations by their values
  - `arrange()` to reorder the rows
  - `select()` to pick variables by their names
  - `mutate()` to create new variables with functions of existing variables
  - `summarise()` to collapse many values down to a single summary
- Can all be used in conjunction with `group_by()`, which changes scope of each function from operating on the entire data set to operating on it group-by-group

- For all the six functions listed above:
  - first argument is a data frame
  - subsequent arguments describe what to do with the data farm, using variable names without quotes
  - result is new data frame
- can chain together multiple simple steps to achieve complex result
- will never change the passed in data frame

###### Filter rows with `filter()`
- allows me to subset observations based on their values
  - 1st arg is data frame
  - 2nd and subsequent args are expressions that filter the data frame
- i.e., `filter(flights, month == 1, day == 1)`
- can manipulate using `&`, `|`, and `!`
- i.e, `nov_dec <- filter(flights, month %in% c(11, 12))` is equivalent to `filter(flights, month == 11 | month == 12)` but is not equivalent to `filter(flights, month == 11 | 12)`
- do not use `&&` or `||`, these are for condition execution in R
- NA represents missing values, `NA == NA` is `NA`, rather than `TRUE`
- `is.na(x)` is easiest way to tell if x is `NA`
- `filter()` will exclude `NA` and `FALSE` by default and only return rows that are `TRUE`


