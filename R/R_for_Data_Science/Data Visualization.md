#### Data Visualization

- ggplot2 is most elegant and versatile system in R to make graphs
- part of tidyverse
- `install.packages("tidyverse")` | `library(tidyverse)`
- [The Layered Grammar of Graphics](http://vita.had.co.nz/papers/layered-grammar.pdf)

How to use ggplot2 to make graphs?
###### Prerequisites
- to be explicit about where function or dataset comes from, use special form `package::function()`
- i.e., `ggplot2::ggplot2()`

`ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy))`
- ggplot always takes a data argument, set to the data set being used, as well as one or more layers
  - geom_point is a layer added to ggplot that we provide a mapping (defines how variables in dataset are mapped to visual properties)
  - mapping argument is always paired with aes(), where x and y are arguments of aes and specify which variables map to x and y axis
- `ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, color = class))`
  - this is best way to show a third variable like class in a 2d graph
  - also could use shape, size, alpha (transparency), etc but these are not recommended for discrete variables

###### Facets
- can add additional variables using aesthetics, but can also use facets
- facets are subplots that each display one subset of data
- `facet_wrap()`
  - first arg should be a formula, denoted by ~ followed by variable name.
    - this variable needs to be discrete

`ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + facet_wrap(~ class, nrow = 2)`
- `facet_grid` vs `facet_wrap`
  - `facet_grid` takes two arguments in the formula (first) arg, rather than 1. can use `.` instead of row or column
  - `facet_wrap` takes 1 arg, as well as `nrow` or `ncol` arg (`facet_grid` does not take `nrow` or `ncol` args)
- screens are rectangular, therefore put variable with more levels in the column so it spreads wide rather than long

###### Geometric Objects
- geom is a geometric object that a plot uses to represent data
- ppl describe plots by type of geom that the plot uses
  - bar charts : bar geoms
  - line charts : line geoms
  - boxplots : boxplot geoms
  - scatterplots : point geoms
- i.e., `ggplot(data = mpg) + geom_smooth(mapping = aes(x = displ, y = hwy))`
- not every aesthetic is supported by every geom!
- i.e., shape is not supported by geom_smooth, while it is supported by geom_point
`ggplot(data = mpg) + geom_smooth(mapping = aes(x = displ, y = hwy, linetype = drv))`
- can also overlay multiple geoms!
- i.e., `ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_point() + geom_smooth()`

###### Statistical Transformations
Some geoms will display a count of a bin.
- bar charts, historygrams, and frequency polygons will do this
- i.e.,`ggplot(data = diamonds) + stat_count(mapping = aes(x = cut))`, substituting `stat_count` in for `geom_bar`

###### Coordinate systems
Most complicated part of ggplot
- default is cartesian, there are various others
- coord_flip() switches the x and y axis
  - i.e., `ggplot(data=mpg, mapping = aes(x = class, y = hwy)) + geom_boxplot() + coord_flip()`
- `coord_quickmap()` will set aspect ratio correctly for maps
  - important if plotting spacial data
- `coord_polar()` uses polar coordinates, reveals interesting connection between bar chart and coxcomb chart

Can use the template to build any plot you want!
